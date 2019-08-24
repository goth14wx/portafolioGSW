<template>
<span style="display:inline-block; color:green !important; font-weigth:bold"  v-waypoint="{ active: true, callback: onWaypoint, options: intersectionOptions }" :class="this.customClass" ></span>
</template>

<script>
import Typed from 'typed.js';

export default {
  props:['txt','sliceTxt','Color','customClass'],
  data(){
    return{
      barColor: this.Color ? this.Color : true,
      typed:true,
      intersectionOptions: {
      root: null,
      rootMargin: '0px 0px 0px 0px',
      thresholds: [0]
    }
    }
  },
  methods:{
    onWaypoint ({ going, direction }) {
        console.log("deberia de tipiar");
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
    
      }
    }
  }
}
</script>