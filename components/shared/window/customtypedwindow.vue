<template>
  <v-card
   class="mx-auto"
   :data-aos="animations[Math.ceil((Math.random()*animations.length))]"
    color="#0B0014"
    dark
    flat
    max-width="900px"
    :id="this.customClass"
    :class="{'animated':true,'shake':shakedActive,'tada':tadaActive}"
  > 
    <v-system-bar style="max-width:900px"  window :color="barColor" max-width="900">
      <span class="text-truncate">{{this.title}} </span>
      <v-spacer></v-spacer>
      <v-icon>remove</v-icon>
      <v-icon>check_box_outline_blank</v-icon>
      <v-icon>close</v-icon>
    </v-system-bar>
    <div :class="{'font-cutive-mono':true,'zoom-in':true}" style="background-color:white; height:auto; font-size:18px">
      <slot></slot>
    </div>
        
  </v-card>
</template>

<script>
import Typed from 'typed.js';
import AOS from 'aos';
export default {
  props:['customClass','Color','Shake','Tada','title'],
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
  mounted(){
   AOS.init();
  }
}
</script>