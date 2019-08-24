<template>

<v-layout row>
    <v-flex lg12>
        <animeTitle1 style="padding-left:15px" :title="'Configurando Virtualhosts'" />
    </v-flex>
    <v-flex lg12>
        <cardParagraph :textCard="textCard" :linksCard="links" :classAdd="'card01'" :fancy="true" />
    </v-flex>
     <v-flex lg12>
         <cardParagraph :textCard="textCardStep1" :classAdd="'card02'" :fancy="true">
             <animeTitle2 :tClass="'step1'" :txtString="' Acerca de . . .'" />
         </cardParagraph>
        <cardParagraph :textCard="textCardStep2" :classAdd="'card03'" :linksCard="linksPort" :fancy="false" />
    </v-flex>
<!----->
    <v-flex lg12>
         <cardParagraph :textCard="textCardStep2" :classAdd="'card04'" :fancy="false" >
             <animeTitle2 :tClass="'step2'" :txtString="'1er Paso - CREAR LA ESTRUCTURA DEL DIRECTORIO'"/>
         </cardParagraph>
         <cardParagraph :textCard="textCardStep3" :classAdd="'card05'"  :fancy="false"/>
       <window :sliceTxt="'sudo '" :rootUser="true" :txt="'sudo mkdir -p /var/www/example.com/public_html'" :customClass="'terminal2'" />
       <br/>
       <window :sliceTxt="'sudo mkdir -p /var/www/example.com/public_html '" :rootUser="true" :txt="'sudo mkdir -p /var/www/test.com/public_html'" :customClass="'terminal3'" />

         <cardParagraph :textCard="textCardStep4" :classAdd="'card06'"  :fancy="false"/>
        <cardParagraph :textCard="textCardStep5" :classAdd="'card07'"  :fancy="false"/>

        <window :sliceTxt="'sudo mkdir -p /var/www/test.com/public_html '" :rootUser="false" :txt="'sudo chown -R $USER:$USER /var/www/example.com/public_html'" :customClass="'terminal4'" />
       <br/>
       <window :sliceTxt="'sudo chown -R $USER:$USER /var/www/example.com/public_html'" :rootUser="false" :txt="'sudo chown -R $USER:$USER /var/www/test.com/public_html'" :customClass="'terminal5'" />
        
        <cardParagraph :textCard="textCardStep6" :classAdd="'card08'"  :fancy="false"/>
        <cardParagraph :textCard="textCardStep7" :classAdd="'card09'"  :fancy="false"/>

        <window :sliceTxt="'sudo chown -R $USER:$USER /var/www/test.com/public_html'" :rootUser="true" :txt="'sudo chmod -R 755 /var/www'" :customClass="'terminal6'" />



        <br/>
        <customModalDialog :video="stepsVideo[0]"/>

    </v-flex>

    <v-flex lg12>
<cardParagraph :textCard="textCardStep8" :classAdd="'card10'" :fancy="false" >
             <animeTitle2 :tClass="'step2'" :txtString="'2do Paso - CREAR PÁGINAS DE PRUEBA PARA CADA VIRTUAL HOST'"/>
         </cardParagraph>

         <cardParagraph :textCard="textCardStep9" :classAdd="'card11'" :fancy="false" />
        
        <window :sliceTxt="'sudo chmod -R 755 /var/www'" :rootUser="true" :txt="'nano /var/www/example.com/public_html/index.html'" :customClass="'terminal07'" />
         
         <cardParagraph :textCard="textCardStep10" :classAdd="'card12'" :fancy="false" />

<customtypedwindow :Color="'blue'" customClass="'terminal08'" :title="'Terminal- /var/www/example.com/public_html/index.html '" >

        <p v-for="(sentence,index) in indexHTML" :key="'indexHTMLs'+index">
            <typed :Color="false" :sliceTxt="''"  :customClass="'terminal0'+(index+9)" :txt="sentence"></typed>
        </p>
        

  </customtypedwindow >

    </v-flex>

<v-flex lg12>
    <cardParagraph :textCard="textCardStep11" :classAdd="'card13'" :fancy="false" >
             <animeTitle2 :tClass="'step3'" :txtString="'3er Paso - CONFIGURANDO VIRTUALHOSTS'"/>
         </cardParagraph>
         
         <window :sliceTxt="'nano /var/www/example.com/public_html/index.html'" :rootUser="true" :txt="'sudo cp /etc/apache2/sites-available/000-default.conf /etc/apache2/sites-available/example.com.conf'" :customClass="'terminal29'" />
        <cardParagraph :textCard="textCardStep12" :classAdd="'card15'" :fancy="false" />

         <window :sliceTxt="'sudo '" :rootUser="true" :txt="'sudo nano /etc/apache2/sites-available/example.com.conf '" :customClass="'terminal30'" />

        <cardParagraph :textCard="textCardStep13" :classAdd="'card16'" :fancy="false" />


         <customtypedwindow :Color="'blue'" customClass="'terminal08'" :title="'Terminal- nano /etc/apache2/sites-available/example.com.conf'" >

            <p style="color:black"> &#60;VirtualHost *:80&#62; </p>
   <span style="color:black">ServerAdmin </span> <typed :Color="false" :sliceTxt="'webmaster@localhost'"  :customClass="'terminal40'" :txt="'admin@example.com'"></typed>
   <br>
   <span style="color:black">ServerName </span> <typed :Color="false" :sliceTxt="''"  :customClass="'terminal41'" :txt="'example.com'"></typed>
   <br>
    <span style="color:black">ServerAlias </span> <typed :Color="false" :sliceTxt="''"  :customClass="'terminal42'" :txt="'www.example.com'"></typed>
    <br>
    <span style="color:black">DocumentRoot </span> <typed :Color="false" :sliceTxt="'/var/www/html'"  :customClass="'terminal43'" :txt="'var/www/example.com/public_html'"></typed>
    <br>
    <span style="color:black">ErrorLog </span> <typed :Color="false" :sliceTxt="''"  :customClass="'terminal44'" :txt="'{APACHE_LOG_DIR}/error.log'"></typed>
    <br>
    <span style="color:black">CustomLog </span> <typed :Color="false" :sliceTxt="''"  :customClass="'terminal45'" :txt="'${APACHE_LOG_DIR}/access.log combined'"></typed>
        <p style="color:black">&#60;/VirtualHost&#62;</p>

  </customtypedwindow >


  <cardParagraph :textCard="textCardStep14" :classAdd="'card20'" :fancy="false" />
</v-flex>

<v-flex lg12>
   <cardParagraph :textCard="textCardStep15" :classAdd="'card21'" :fancy="false" >
             <animeTitle2 :tClass="'step3'" :txtString="'4to Paso - HABILITAR LOS NUEVOS ARCHIVOS VIRTUAL HOST '"/>
         </cardParagraph>
         <window :sliceTxt="'sudo '" :rootUser="true" :txt="'sudo a2ensite example.com.conf &#38;&#38; sudo a2ensite test.com.conf &#38;&#38; sudo a2dissite 000-default.conf '" :customClass="'terminal31'" />
          <cardParagraph :textCard="textCardStep16" :classAdd="'card22'" :fancy="false" />
          <window :sliceTxt="'sudo '" :rootUser="true" :txt="'sudo systemctl restart apache2'" :customClass="'terminal32'" />
           <cardParagraph :textCard="textCardStep17" :classAdd="'card23'" :fancy="false" />
          <window :sliceTxt="'sudo systemctl restart apache2 '" :rootUser="true" :txt="'sudo nano /etc/hosts'" :customClass="'terminal33'" />
          <cardParagraph :textCard="textCardStep18" :classAdd="'card24'" :fancy="false" />

          <customtypedwindow :Color="'blue'" customClass="'terminal34'" :title="'Terminal- nano /etc/apache2/sites-available/example.com.conf'" >

            <p style="color:black"> 127.0.0.1   localhost </p>
            <p style="color:black"> 127.0.1.1   guest-desktop </p>
            
            <typed :Color="false" :sliceTxt="''"  :customClass="'terminal50'" :txt="'127.0.0.1   example.com'"></typed>
            <br/>
            <typed :Color="false" :sliceTxt="''"  :customClass="'terminal51'" :txt="'127.0.0.1   test.com'"></typed>

  </customtypedwindow >

</v-flex>

<v-flex lg12>
    <cardParagraph :textCard="textCardStep19" :classAdd="'card24'" :fancy="false" />
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
            textCard:'Apache divide su funcionalidad y componentes en unidades independientes que pueden ser configuradas independientemente. La unidad básica que describe un sitio individual o el dominio llamado virtual host .',
            links:[
                {
                    to:'https://httpd.apache.org/docs/2.4/vhosts/examples.html',
                    text:'Virtualhosts',
                    color:'pink'
                }
            ],
            linksPort:[
                {
                    to:'https://documentation.cpanel.net/display/CKB/How+Your+Server+Handles+Domains+and+Virtual+Hosts',
                    text:'Como funciona'
                },
                {
                    to:"https://en.wikipedia.org/wiki/Virtual_hosting",
                    text:'mas informacion',
                    color:"red"
                }
            ],
            indexHTML:[
                "&#60;html&#62;",
                " &#60;head&#62;",
                "   &#60;title&#62;¡Bienvenido a Example.com!&#60;/title&#62;",
                "&#60;/head&#62;",
                "&#60;body&#62;",
                "&#60;h1&#62;¡Lo lograste! El virtual host test.com está funcionando&#60;/h1&#62; ",
                "&#60;/body&#62;",
                "&#60;/html&#62;"
            ],
            textCardStep1:"Estas asignaciones permiten al administrador utilizar un servidor para alojar varios dominios o sitios en una simple interface o IP utilizando un mecanismo de coincidencias; esto es relevante para cualquiera que busque alojamiento para más de un sitio en un solo servidor.",
            textCardStep2:"Cada dominio que es configurado apuntará al visitante a una carpeta específica que contiene la información del sitio, nunca indicará que el mismo servidor es responsable de otros sitios. Este esquema es expandible sin límites de software tanto como el servidor pueda soportar la carga.",
            textCardStep3:"Dentro de cada uno de estos directorios, crearemos una carpeta public_html que mantendrá los archivos. Esto nos dará algo de flexibilidad en nuestro hosting. \n Por ejemplo, para nuestros sitios, vamos a crear los directorios así:",
            textCardStep4:'example y test representan los nombres de dominio que deseamos servir desde nuestro servidor web.',
            textCardStep5:'Ahora tenemos la estructura de directorios para nuestros archivos, pero son propiedad de nuestro usuario root. Si queremos que nuestro usuario regular sea capaz de modificar archivos dentro de nuestros directorios web, debemos cambiar la propiedad haciendo lo siguiente:',
            textCardStep6:"La variable $USER tomará el valor del usuario con el cual estás autenticado actualmente cuando presiones Enter. Haciendo esto, nuestro usuario regular ahora será el propietario del directorio public_html y sus respectivos sub-directorios donde almacenaremos nuestro contenido.",
            textCardStep7:"Debemos, además, modificar un poco nuestros permisos para asegurarnos de que el acceso de lectura esté habilitado en el directorio web general y todos los archivos y directorios en él para que todas las páginas puedan ser servidas correctamente:",
            textCardStep8:"Vamos a ir con una demostración, así que nuestras páginas serán muy simples. Vamos a crear una página index.html para cada sitio.",
            textCardStep9:"Vamos a ir con una demostración, así que nuestras páginas serán muy simples. Vamos a screar una página index.html para cada sitio. \n Vamos a empezar con example.com . Podemos abrir un archivo index.html en nuestro editor escribiendo:",
            textCardStep10:"En éste archivo, crea un documento HTML simple que indica el sitio al cual está conectado. El archivo quedaría así:",
            textCardStep11:"Vamos a iniciar con un dominio, configurarlo, copiarlo para nuestro segundo dominio, y después hacer algunos cambios para ajustes tanto como se requieran. La configuración por defecto de Ubuntu requiere que cada archivo de virtual host termine en .conf.",
            textCardStep12:"Abra el nuevo archivo en su editor con permisos de root: ",
            textCardStep13:"El archivo se verá algo así (se han removido los comentarios aquí para hacer el contenido más apreciable):",
            textCardStep14:"Siga los mismos pasos para el virtualhost de test",
            textCardStep15:"Ahora que hemos creado nuestros archivos de virtual host, debemos habilitarlos. Apache incluye algunas herramientas que nos permiten hacer esto. Podemos usar la herramienta a2ensite para habilitar cada uno de nuestros sitios así:",
            textCardStep16:"Cuando concluyas, deberá reiniciar Apache para hacer que estos cambios sean efectivos: ",
            textCardStep17:"Edite su archivo local con privilegios de administrador escribiendo:",
            textCardStep18:"Para los dominios que han usado en esta guía, se agregan las siguientes líneas en la parte inferior del archivo hosts:",
            textCardStep19:"Es todo, ahora ya puedes ver tus sitios web, en las siguientes direcciones example.com y test.com"
            
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

