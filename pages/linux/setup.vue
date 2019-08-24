<template>

<v-layout row>
    <v-flex lg12>
        <animeTitle1 style="padding-left:15px" :title="'Preparando todo'" />
    </v-flex>
    <v-flex lg12>
        <cardParagraph :textCard="textCard" :linksCard="links" :classAdd="'card01'" :fancy="true" />
    </v-flex>
     <v-flex lg12>
         <cardParagraph :textCard="textCardStep1" :classAdd="'card02'" :fancy="true">
             <animeTitle2 :tClass="'step1'" :txtString="'1er Paso - INICIAR SESIÓN COMO USUARIO «ROOT»'" />
         </cardParagraph>
       <window :sliceTxt="'sudo apt-get install'" :txt="'sudo su'" :customClass="'terminal1'" />
    </v-flex>

    <v-flex lg12>
         <cardParagraph :textCard="textCardStep2" :classAdd="'card03'" :fancy="false" >
             <animeTitle2 :tClass="'step2'" :txtString="'2do Paso - CREAR UN NUEVO USUARIO'"/>
         </cardParagraph>
       <window :sliceTxt="'sudo su'" :rootUser="true" :txt="'adduser gsw'" :customClass="'terminal2'" />
    </v-flex>

<v-flex lg12>
         <cardParagraph :textCard="textCardStep3" :classAdd="'card04'" :fancy="false" >
             <animeTitle2 :tClass="'step4'" :txtString="'3er Paso — CONCESIÓN DE PRIVILEGIOS ADMINISTRATIVOS'"/>
         </cardParagraph>
       <window :sliceTxt="'adduser gsw'" :rootUser="true" :txt="'usermod -aG sudo gsw'" :customClass="'terminal3'" />
    </v-flex>

    <v-flex lg12>
         <cardParagraph :textCard="textCardStep4" :classAdd="'card05'" :fancy="false"/>
       <window :sliceTxt="'usermod -aG sudo gsw'" :rootUser="true" :txt="'su gsw'" :customClass="'terminal4'" />
    </v-flex>

    <v-flex lg12>
         <cardParagraph :textCard="textCardStep5" :classAdd="'card06'" :fancy="false"/>
       <window :sliceTxt="'su gsw'" :rootUser="true" :txt="'whoami'" :customClass="'terminal5'" />
    </v-flex>

    <v-flex lg12>
         <cardParagraph :textCard="textCardStep6" :classAdd="'card07'"  :fancy="false">
         <animeTitle2 :tClass="'step4'" :txtString="'4to Paso — CONFIGURACIÓN DE UN CORTAFUEGOS BÁSICO'"/>
         </cardParagraph>
         <cardParagraph :textCard="textCardStep7" :classAdd="'card08'" :linksCard="linksUFW" :fancy="false"/>
       <window :sliceTxt="'whoami'" :rootUser="true" :txt="'ufw app list'" :Color="''" :customClass="'terminal6'" />
       <br/>
    <customModalDialog :video="stepsVideo[0]"/>
    </v-flex>

     <v-flex lg12>
         <br>
         <alert :txt="error1" :Color="'#D50000'" :Danger="true"/>
       <window :sliceTxt="'ufw allow OpenSSH'" :Shake="true"  :rootUser="true" :txt="'ufw: command not found'" :Color="'#D50000'" :customClass="'terminal7'" />
       <br/>
       <alert :txt="solution1" :Color="'#2196F3'" :Primary="true"/>
       <window :sliceTxt="'ufw: command not found'" :txt="'apt-get install openssh-server'" :Tada="true" :rootUser="true"  :Color="'#2196F3'" :customClass="'terminal8'" />
    </v-flex>

    <v-flex lg12>
         <cardParagraph :textCard="textCardStep8" :classAdd="'card09'" :fancy="false"/>
       <window :sliceTxt="'apt-get install openssh-server'" :rootUser="true" :txt="'ufw allow OpenSSH'" :customClass="'terminal9'" />
    </v-flex>

    <v-flex lg12>
         <cardParagraph :textCard="textCardStep9" :classAdd="'card10'" :fancy="false"/>
       <window :sliceTxt="'ufw allow OpenSSH'" :rootUser="true" :txt="'ufw enable'" :customClass="'terminal10'" />
    </v-flex>

     <v-flex lg12>
         <cardParagraph :textCard="textCardStep10" :classAdd="'card11'" :fancy="false"/>
       <window :sliceTxt="'ufw enable'" :rootUser="true" :txt="'ufw status'" :customClass="'terminal11'" />
       <br/>
       <customModalDialog :video="stepsVideo[1]"/>
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
            imgs:["https://i.imgur.com/ovIRysD.gif"],
            stepsVideo:['https://www.youtube.com/embed/RvKoq2ckAFE','https://www.youtube.com/embed/VWVLnAOriBk'],
            textCard:'Instalaremos xampp en nuestra maquina virtual linux, utilizando ubuntu 16.04, recomiendo utilizar zorin os 12 lite, debido a que es la distro mas estable que he probado',
            links:[
                {
                    to:'https://zorinos.com/download/12/lite/',
                    text:'Zorin os 12 lite',
                    color:'pink'
                },
                {
                    to:'http://releases.ubuntu.com/16.04/',
                    text:'ubuntu 16.04'
                },
            ],
            linksUFW:[{
                to:'https://wiki.ubuntu.com/UncomplicatedFirewall',
                text:'ufw site',
                color:'pink'
            },
            {
                to:'http://gufw.org/',
                text:'aplicacion grafica ufw',
                color:'primary'
            }],
            error1:"Si aparece un mensaje como el siguiente: ",
            solution1:"instala el paquete con: ",
            textCardStep1:"El usuario «ROOT» es el usuario administrativo en un entorno Linux que tiene privilegios muy amplios. Debido a los mayores privilegios de la cuenta «ROOT», se recomienda no utilizarla regularmente. Esto se debe a que parte del poder inherente de la cuenta «ROOT» es la capacidad de realizar cambios que podrían resultar muy destructivos, incluso en forma accidental. El siguiente paso es configurar una cuenta de usuario alternativa con un alcance reducido para el trabajo cotidiano. Le enseñaremos cómo obtener mayores privilegios en los momentos en que los necesite.",
            textCardStep2:"Una vez que haya iniciado sesión como «ROOT», estará preparado para agregar la nueva cuenta de usuario que usará para iniciar sesión de ahora en adelante. Este ejemplo crea un nuevo usuario llamado «gsw», pero debe reemplazarlo con el nombre de usuario de su preferencia:",
            textCardStep3:"Para agregar estos privilegios a nuestro nuevo usuario, necesitamos agregar el nuevo usuario al grupo «sudo». De forma predeterminada, Ubuntu 16.04-18.04 permite que los usuarios que pertenecen al grupo «sudo» usen el comando «sudo». Desde la cuenta «ROOT», ejecute este comando para agregar su nuevo usuario al grupo «sudo»",
            textCardStep4:"Para cambiar de usuario en la terminal escribimos:",
            textCardStep5:"Ingresamos la contraseña establecida, para verificar en que usuario estamos, escribimos el comando de:",
            textCardStep6:"Los servidores Ubuntu 16.04-18.04 pueden usar el cortafuegos UFW para asegurarse de que solo se permitan conexiones a ciertos servicios. Podemos configurar un cortafuegos básico muy fácilmente con esta aplicación.",
            textCardStep7:"Las diferentes aplicaciones pueden registrar sus perfiles en UFW después de la instalación. Estos perfiles permiten a UFW administrar estas aplicaciones por nombre. OpenSSH, el servicio que nos permite conectarnos a nuestro servidor ahora tiene un perfil registrado en UFW.",
            textCardStep8:"Necesitamos asegurarnos de que el cortafuegos permita conexiones SSH para que podamos volver a iniciar sesión la próxima vez. Podemos permitir estas conexiones si escribimos:",
            alert1:"Nota: Si la terminal nos indica: ufw: command not found , nos esta indicando que no tenemos cortafuegos instalado.",
            textCardStep9:"Seguidamente, podemos habilitar el cortafuegos si escribimos:",
            textCardStep10:"Escriba «y» y presione «ENTER» para avanzar. Puede ver que estas conexiones SSH aún están permitidas si escribe:"

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

