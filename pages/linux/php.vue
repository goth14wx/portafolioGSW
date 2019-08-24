<template>

<v-layout row>
    <v-flex lg12>
        <animeTitle1 style="padding-left:15px" :title="'Instalando PHP 7.0'" />
    </v-flex>
    <v-flex lg12>
        <cardParagraph :textCard="textCard" :linksCard="links" :classAdd="'card01'" :fancy="true" />
    </v-flex>
     <v-flex lg12>
         <cardParagraph :textCard="textCardStep1" :classAdd="'card02'" :fancy="true">
             <animeTitle2 :tClass="'step1'" :txtString="'1er Paso - INSTALAR PHP'" />
         </cardParagraph>
       <window :sliceTxt="'sudo apt-get install'" :txt="'sudo apt install php libapache2-mod-php php-mysql'" :customClass="'terminal1'" />
    </v-flex>
<!----->
    <v-flex lg12>
         <cardParagraph :textCard="textCardStep2" :classAdd="'card03'" :linksCard="linksPort" :fancy="false" >
             <animeTitle2 :tClass="'step2'" :txtString="'2do Paso - Configurando PHP'"/>
         </cardParagraph>
         <cardParagraph :textCard="textCardStep3" :classAdd="'card04'"  :fancy="false"/>
       <window :sliceTxt="'sudo apt install php libapache2-mod-php php-mysql'" :rootUser="true" :txt="'sudo nano /etc/apache2/mods-enabled/dir.conf'" :customClass="'terminal2'" />

         <cardParagraph :textCard="textCardStep4" :classAdd="'card05'"  :fancy="false"/>
         
        <customtypedwindow :Color="'blue'" customClass="'terminal3'" :title="'Terminal- nano /etc/apache2/mods-enabled/dir.conf'" >

        <p style="color:black"> &#60;IfModule mod_dir.c&#62; </p>

        <span style="color:black"> DirectoryIndex </span>
        <typed :Color="true" :sliceTxt="'index.html'" :customClass="'terminal4'" :txt="'index.php'"></typed>
        <span style="color:black"> index.cgi index.pl </span>
         <typed :sliceTxt="'index.php'" :customClass="'terminal5'" :txt="'index.html'"></typed>
        <span style="color:black"> index.xhtml </span>
         <p style="color:black"> &#60;IfModule&#62; </p>

            </customtypedwindow >
        <cardParagraph :textCard="textCardStep5" :classAdd="'card05'"  :fancy="false"/>
        <br/>
        <customModalDialog :video="stepsVideo[0]"/>

    </v-flex>




</v-layout>

</template>


<script>
import animeTitle1 from '@/components/shared/customTitles/animeTitle1';
import animeTitle2 from '@/components/shared/customTitles/animeTitle2';
import cardParagraph from '@/components/shared/cardParagraph';
import window from '@/components/shared/window';
import customtypedwindow from '@/components/shared/window/customtypedwindow';
import typed from '@/components/shared/window/typed';
import alert from '@/components/shared/alert';
import customModalDialog from '@/components/shared/customModalDialog';
export default {
    data(){
        return{
            stepsVideo:['https://www.youtube.com/embed/KkMVMKG6Sco'],
            textCard:'PHP es el componente de tu configuración que procesa código para desplegar contenido dinámico. Puede ejecutar archivos, conectarse a tus bases de datos MySQL para obtener información, y manejar la visualización del contenido procesado sobre tu servidor web',
            links:[
                {
                    to:'https://www.php.net/',
                    text:'PHP',
                    color:'pink'
                }
            ],
            linksPort:[
                {
                    to:'https://www.wordfence.com/learn/understanding-php-vulnerabilities/',
                    text:'Exploits comunes de PHP'
                },
                {
                    to:"https://www.cvedetails.com/vulnerability-list/vendor_id-74/product_id-128/PHP-PHP.html",
                    text:'Vulnerabilidades PHP',
                    color:"red"
                }
            ],
            textCardStep1:"Una vez más usaremos el sistema apt para instalar PHP. Adicionalmente lo podemos configurar para que se ejecute sobre el servidor Apache y para que se comunique con la base de datos MySQL:",
            textCardStep2:"En la mayoría de los casos, desearás modificar la forma mediante la cual Apache sirve archivos cuando un directorio es solicitado. En este momento, si un usuario solicita un directorio del servidor, Apache buscará, en primera instancia, un archivo llamado index.html. Si se desea que el servidor web le dé prelación a los archivos PHP sobre cualquier otro archivo. Para lo cual haremos que el Apache busque el archivo index.php en primer lugar.",
            textCardStep3:"Para lograrlo, digita el siguiente comando para abrir el archivo dir.conf en un editor de texto con privilegios de superusuario:",
            textCardStep4:'Debería verse semejante a esto:',
            textCardStep5:'Mueve el archivo de índice de PHP (subrayado arriba) a la primera posición después de la especificación DirectoryIndex.'
            
        }
    },
    components:{
animeTitle1,
animeTitle2,
cardParagraph,
window,
customModalDialog,
alert,
customtypedwindow,
typed
    }

}
</script>

-+