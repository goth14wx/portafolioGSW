<template>

<v-layout row>
    <v-flex lg12>
        <animeTitle1 style="padding-left:15px" :title="'Instalando apache'" />
    </v-flex>
    <v-flex lg12>
        <cardParagraph :textCard="textCard" :linksCard="links" :classAdd="'card01'" :fancy="true" />
    </v-flex>
     <v-flex lg12>
         <cardParagraph :textCard="textCardStep1" :classAdd="'card02'" :fancy="true">
             <animeTitle2 :tClass="'step1'" :txtString="'1er Paso - INSTALAR APACHE'" />
         </cardParagraph>
       <window :sliceTxt="'sudo apt-get install'" :txt="'sudo apt install apache2'" :customClass="'terminal1'" />
    </v-flex>

    <v-flex lg12>
         <cardParagraph :textCard="textCardStep2" :classAdd="'card03'" :fancy="false" >
             <animeTitle2 :tClass="'step2'" :txtString="'2do Paso - AJUSTE DEL CORTAFUEGOS PARA PERMITIR EL TRÁFICO WEB'"/>
         </cardParagraph>
       <window :sliceTxt="'sudo apt install apache2'" :rootUser="true" :txt="'sudo ufw app list'" :customClass="'terminal2'" />

         <cardParagraph :textCard="textCardStep3" :classAdd="'card04'" :linksCard="linksPort" :fancy="false"/>
        <window :sliceTxt="'sudo ufw app list'"  :rootUser="true" :txt="'sudo ufw app info \'Apache Full\''" :customClass="'terminal3'" />

         <cardParagraph :textCard="textCardStep4" :linksCard="linksHTTPHTTPS" :classAdd="'card05'" :fancy="false"/>
        <window :sliceTxt="'sudo ufw app info \'Apache Full\''"  :rootUser="true" :txt="'sudo ufw app allow \'Apache Full\''" :customClass="'terminal4'" />

         <cardParagraph :textCard="textCardStep5" :classAdd="'card06'" :fancy="false"/>
        <window :sliceTxt="'sudo ufw app allow \'Apache Full\''"  :rootUser="true" :txt="'sudo systemctl status apache2'" :customClass="'terminal5'" />

        <cardParagraph :textCard="textCardStep6" :classAdd="'card07'" :fancy="false"/>

    </v-flex>

<v-flex lg12>
         <cardParagraph :textCard="textCardStep7" :classAdd="'card08'" :linksCard="linksConfigApache" :fancy="false" >
             <animeTitle2 :tClass="'step4'"  :txtString="'3er Paso — CONFIGURACIONES BÁSICAS DE SEGURIDAD EN APACHE.'"/>
         </cardParagraph>
       <window :sliceTxt="'sudo systemctl status apache2'" :rootUser="true" :txt="'sudo nano /etc/apache2/conf-enabled/security.conf'" :customClass="'terminal6'" />
        <cardParagraph :textCard="textCardStep8" :classAdd="'card09'" :fancy="false"/>
        <alert :txt="solution1" :Color="'#2196F3'" :Primary="true"/>
         <cardParagraph :textCard="textCardStep9" :classAdd="'card10'" :fancy="false"/>
          <cardParagraph :textCard="textCardStep10" :classAdd="'card11'" :fancy="false"/>
    </v-flex>

    <v-flex lg12>
         <cardParagraph :textCard="textCardStep11" :classAdd="'card012'"  :fancy="false">
         <animeTitle2 :tClass="'step4'" :txtString="'4to Paso — OPTIMIZACIÓN BÁSICA DE APACHE.'"/>
         </cardParagraph>
       <window :sliceTxt="'sudo nano /etc/apache2/conf-enabled/security.conf'" :rootUser="true" :txt="'sudo nano /etc/apache2/apache2.conf'" :Color="''" :customClass="'terminal7'" />
       <cardParagraph :textCard="textCardStep12" :classAdd="'card13'" :fancy="false"/>
       <alert :txt="solution2" :Color="'#2196F3'" :Primary="true"/>
       <cardParagraph :textCard="textCardStep13" :classAdd="'card14'" :fancy="false"/>
       <alert :txt="solution3" :Color="'#2196F3'" :Primary="true"/>

       <cardParagraph :textCard="textCardStep14" :classAdd="'card15'" :fancy="false"/>
        <window :sliceTxt="'sudo nano /etc/apache2/apache2.conf'" :rootUser="true" :txt="'/etc/init.d/apache2 reload'" :Color="''" :customClass="'terminal8'" />
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
            stepsVideo:['https://www.youtube.com/embed/AIslRC6L494'],
            textCard:'El servidor web, Apache es uno de los servidores web más populares en el mundo. Se encuentra bien documentado y ha sido utilizado en buena parte de la historia de la web, hechos que lo convierten en un muy buen candidato para ser escogido como el servidor por defecto de páginas web.',
            links:[
                {
                    to:'https://www.apache.org/',
                    text:'Apache',
                    color:'pink'
                }
            ],
            linksPort:[
                {
                    to:'https://es.wikipedia.org/wiki/Anexo:N%C3%BAmeros_de_puertos_de_red',
                    text:'Puertos'
                }
            ],
            linksHTTPHTTPS:[
                {
                    to:'https://es.godaddy.com/blog/diferencia-entre-http-y-https/',
                    text:'HTTP / HTTPS',
                    color:"orange"
                }
            ],
            linksConfigApache:[
                {
                    to:'http://luismido.wikidot.com/directivas-basicas-de-configuracion-de-apache-2',
                    text:'Directivas APACHE',
                    color:"green"
                }
            ],
            solution1:"ServerTokens Prod \n ServerSignature Off",
            solution2:"Timeout 150 \n MaxKeepAliveRequests 150 \n KeepAliveTimeout 3",
            solution3:"/etc/init.d/apache2 restart \n /etc/init.d/apache2 stop \n /etc/init.d/apache2 start",
            textCardStep1:"Instala Apache usando el administrador de paquetes de Ubuntu, apt:",
            textCardStep2:"Asumiendo que seguiste las instrucciones de configuración inicial del servidor y que habilitaste el cortafuegos UFW, ahora podrás asegurarte que tu cortafuegos permite el tráfico HTTP y HTTPS. Para hacerlo, verifica que el UFW tiene un perfil de aplicación para Apache mediante el comando:",
            textCardStep3:"Si solicitas la información del perfil Apache Full, se debería mostrar que el tráfico se encuentra habilitado para los puertos 80 y 443 :",
            textCardStep4:"Para permitir el tráfico de entrada HTTP y HTTPS para este perfil, digita:",
            textCardStep5:"Verifique con el sistema systemd init para asegurarse de que el servicio se está ejecutando escribiendo:",
            textCardStep6:"Puedes hacer una comprobación instantánea de que todo ha ido según lo planeado visitando la dirección localhost de tu servidor en un navegador.",
            textCardStep7:"A continuación, realizaremos varias modificaciones de los ajustes por defecto de Apache, para hacerlo un poco más seguro y no dar información útil a posibles usuarios malintencionados. Lo primero será editar el archivo de configuración destinado a los ajustes de seguridad, para esto ejecutamos el comando:",
            textCardStep8:"Dentro del contenido buscamos las variables ServerSignature y ServerTokens, de forma que sus valores queden como mostramos a continuación:",
            textCardStep9:"Con la opción ServerTokens Simple o Minimal sólo mostraremos en las cabeceras de las peticiones HTTP que nuestro servidor es Apache, sin mostrar versión ni sistema operativo.",
            textCardStep10:"Con la opción ServerSignature Off evitamos que se muestre un pie de página en los documentos generados por el servidor. Estos pies de página incluyen la versión del servidor y sistema operativo, por ello es aconsejable mantener estos datos ocultos.",
            textCardStep11:"A continuación, realizaremos varias modificaciones en el archivo de configuración general de Apache para tratar de conseguir un mejor rendimiento. Ejecutaremos el siguiente comando:",
            textCardStep12:"Ajustaremos los valores de las siguientes variables como se indica a continuación:",
            textCardStep13:"Para reiniciar/parar/iniciar Apache podemos emplear los comandos:",
            textCardStep14:"Si lo que queremos es reiniciar únicamente la configuración de Apache, es suficiente ejecutar el comando:"

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

