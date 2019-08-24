<template>
  <v-card
   class="mx-auto"
   :data-aos="animations[Math.ceil((Math.random()*animations.length))]"
    color="#0B0014"
    dark
    flat
    max-width="900px"
    :id="this.customClass"
    v-waypoint="{ active: true, callback: onWaypoint, options: intersectionOptions }"
    :class="{'animated':true,'shake':shakedActive,'tada':tadaActive}"
  > 
    <v-system-bar style="max-width:900px"  window :color="barColor" max-width="900">
      <span class="text-truncate">Terminal - usuarioLinux@pcusuario:~$ </span>
      <v-spacer></v-spacer>
      <v-icon>remove</v-icon>
      <v-icon>check_box_outline_blank</v-icon>
      <v-icon>close</v-icon>
    </v-system-bar>
    <div :class="{'font-cutive-mono':true,'zoom-in':true}" style="background-color:black; height:200px; font-size:18px">
      <span style="color:dodgerblue">usuarioLinux@usuario-pc-3543:~{{this.prompt}}</span> <span :class="this.customClass" ></span>
    </div>
        
  </v-card>
</template>

<script>
import Typed from 'typed.js';
import AOS from 'aos';
export default {
  props:['txt','sliceTxt','rootUser','customClass','Color','Shake','Tada'],
  data(){
    return{
      barColor: this.Color ? this.Color : 'pink',
      typed:true,
      prompt : this.rootUser ? "#" : "$",
      animations:['zoom-in-up','fade-up','fade-right','fade-left','fade-up-left','fade-down-right','fade-down-left'],
      intersectionOptions: {
      root: null,
      rootMargin: '0px 0px 0px 0px',
      thresholds: [0],
     
    } ,
     shake:this.Shake ? this.Shake : false,
      shakedActive: false,
      tada : this.Tada ? this.Tada : false,
      tadaActive: false
    }
  },
  methods:{
   showUpTerminal(d){
      // event data
       /*try {
          if(this.typed && d.detail.attributes[2].nodeValue+"" == this.customClass){
       new Typed('.'+this.customClass, {
      strings: [this.sliceTxt, this.txt],
      typeSpeed: 50,
      backSpeed:50
      });
      this.typed=false;
       }
       } catch (error) {
         
       }*/
    },
    onWaypoint ({ going, direction }) {
      // going: in, out
      // direction: top, right, bottom, left
      if (going === this.$waypointMap.GOING_IN) {
        if(this.typed){
       new Typed('.'+this.customClass, {
      strings: [this.sliceTxt, this.txt],
      typeSpeed: 50,
      backSpeed:50
      });
      this.typed=false;
       }
       if(this.shake){
this.shakedActive=true;
       }

        if(this.tada){
this.tadaActive=true;
       }
    
      }
    }
  },
  created(){
     //document.addEventListener('aos:in', this.showUpTerminal)
  },
  mounted(){
   AOS.init();
  }
}
</script>