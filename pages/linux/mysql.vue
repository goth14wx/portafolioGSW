<template>

<v-layout row>
    <v-flex lg12>
        <animeTitle1 style="padding-left:15px" :title="'Instalando MYSQL'" />
    </v-flex>
    <v-flex lg12>
        <cardParagraph :textCard="textCard" :linksCard="links" :classAdd="'card01'" :fancy="true" />
    </v-flex>
     <v-flex lg12>
         <cardParagraph :textCard="textCardStep1" :classAdd="'card02'" :fancy="true">
             <animeTitle2 :tClass="'step1'" :txtString="'1er Paso - INSTALAR MYSQL'" />
         </cardParagraph>
       <window :sliceTxt="'sudo apt-get install'" :txt="'sudo apt install mysql-server'" :customClass="'terminal1'" />
    </v-flex>
<!----->
    <v-flex lg12>
         <cardParagraph :textCard="textCardStep2" :classAdd="'card03'" :linksCard="linksPort" :fancy="false" >
             <animeTitle2 :tClass="'step2'" :txtString="'2do Paso - Configurando MYSQL'"/>
         </cardParagraph>
       <window :sliceTxt="'sudo apt install mysql-server'" :rootUser="true" :txt="'sudo mysql_secure_installation'" :customClass="'terminal2'" />

         <cardParagraph :textCard="textCardStep3" :classAdd="'card04'"  :fancy="false"/>
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
import alert from '@/components/shared/alert';
import customModalDialog from '@/components/shared/customModalDialog';
export default {
    data(){
        return{
            stepsVideo:['https://www.youtube.com/embed/SsEBgZoMBng'],
            textCard:'Ahora que tienes tu servidor web activo y funcional, es el momento de instalar MySQL. MySQL es un sistema de administración de bases de datos. Básicamente, él organizará y proveerá acceso a las bases de datos donde tu sitio podrá guardar información.',
            links:[
                {
                    to:'https://www.mysql.com/',
                    text:'MYSQL',
                    color:'pink'
                }
            ],
            linksPort:[
                {
                    to:'https://www.owasp.org/index.php/Reviewing_MySQL_Security',
                    text:'Exploits comunes de MYSQL'
                },
                {
                    to:"https://www.cvedetails.com/vulnerability-list/vendor_id-185/product_id-316/Mysql-Mysql.html",
                    text:'Vulnerabilidades MYSQL',
                    color:"red"
                }
            ],
            textCardStep1:"Instala Apache usando el administrador de paquetes de Ubuntu, apt:",
            textCardStep2:"Cuando la instalación esté completa, debes ejecutar un archivo de comandos de seguridad que viene preinstalado con MySQL, éste removerá algunos parámetros peligrosos, así como asegurará el acceso a tu base de datos. Ejecuta el archivo interactivo de comandos mediante:",
            textCardStep3:"Se te preguntará si quieres configurar el conector de validación de contraseña: VALIDATE PASSWORD PLUGIN. Responde Y si estás de acuerdo, cualquier otra respuesta continuará sin realizar la habilitación.",
            
        }
    },
    components:{
animeTitle1,
animeTitle2,
cardParagraph,
window,
customModalDialog,
alert
    }

}
</script>

