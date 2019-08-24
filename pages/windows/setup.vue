<template>

<v-layout row>
    <v-flex lg12>
        <animeTitle1 style="padding-left:15px" :title="'Instalando IIS'" />
    </v-flex>
    <v-flex lg12>
        <cardParagraph :textCard="textCard" :linksCard="links" :classAdd="'card01'" :fancy="true" />
    </v-flex>
     <v-flex lg12>
         <cardParagraph :textCard="textCardStep1" :classAdd="'card02'" :fancy="true">
             <animeTitle2 :tClass="'step1'" :txtString="'1er Paso - INSTALAR IIS'" />
         </cardParagraph>
         <customModalDialog :video="stepsVideo[0]"/>
         <br>
    </v-flex>
<!----->
    <v-flex lg12>
         <cardParagraph :textCard="textCardStep2" :classAdd="'card03'"   :fancy="false" >
             <animeTitle2 :tClass="'step2'" :txtString="'2do Paso - Verificando IIS'"/>
         </cardParagraph> 

         <cardParagraph :textCard="textCardStep3" :classAdd="'card04'"  :fancy="false"/>
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
            stepsVideo:['https://www.youtube.com/embed/nCFSxfywhlg','https://www.youtube.com/embed/sbhGw0eHaPQ'],
            textCard:'Todas las versiones de Windows incluyen un servidor web local, llamado: "Internet Information Services", Es muy conocido por las siglas IIS. IIS es poco conocido y utilizado por los usuarios de Windows, los que en ocasiones descargan programas externos para instalar un servidor, sin saber que poseen uno en el sistema.',
            links:[
                {
                    to:'https://www.iis.net/',
                    text:'IIS',
                    color:'pink'
                }
            ], 
            textCardStep1:"En las instalaciones de Windows los archivos necesarios para funcionar IIS están incluidos en el sistema, aunque no viene instalado el servidor de forma predeterminada.",
            textCardStep2:"CUna vez que haya instalado el IIS y de manera que pueda crear proyectos, abra el administrador del IIS (IIS Manager) o ubicando el acceso Internet Information Services (IIS) Manager desde la carpeta de las Herramientas administrativas (Administrative tools), accedido desde Panel de Control-> Sistema y seguridad.",
            textCardStep3:"Confirme que el servidor web funciona abriendo un navegador web y verifique que se muestre la siguiente página web predeterminada cuando utilice la dirección http://localhost.",
            
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

