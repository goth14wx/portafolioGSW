<template>
  <div>
    <v-alert
      border="left"
      colored-border
      :color="this.coolor"
      flat
      max-width="900"
      class=" mx-auto white--text font-livvic"
      :class="{'danger':this.danger,'animated bounceIn':Animated,'primary':this.primary}"
      v-waypoint="{ active: true, callback: onWaypoint, options: intersectionOptions }"
      style="white-space: pre-line"
    >
      {{ Text }}
    </v-alert>
  </div>
</template>

<script>
export default {
    props:['txt','Color','Danger','Primary'],
    data(){
        return{
            Text: this.txt ? this.txt : '',
            coolor : this.Color ? this.Color : '#2196F3',
            danger: this.Danger ? this.Danger : false,
            primary: this.Primary ? this.Primary : false,
            animations:['zoom-in-up','fade-up','fade-right','fade-left','fade-up-left','fade-down-right','fade-down-left'],
            Animated:false,
      intersectionOptions: {
      root: null,
      rootMargin: '0px 0px 0px 0px',
      thresholds: [0]
    } ,
        }
    },
    methods:{
       onWaypoint ({ going, direction }) {
this.Animated=true;
    }
    }
}
</script>

<style>

.danger{
    background: linear-gradient(to right, #e52d27, #b31217); 
}

.primary{
    background: linear-gradient(to right, #00c6ff, #0072ff);
}

</style>