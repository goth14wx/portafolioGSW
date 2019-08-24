<template>
    <div :data-aos="animations[Math.ceil((Math.random()*animations.length))]" :id="this.targetClass">
    <h1 :class="this.tClass" >
  <span v-for="(txt,index) in textString" :key="targetClass+index" class="word pl-0 font-livvic">{{txt}}&nbsp</span>
</h1>
    </div>
</template>

<script>
import AOS from 'aos';
export default {
    props:['txtString','tClass'],
    data(){
        return{
            textString: this.txtString ? this.txtString.split(" ") : "nothing yet".split(" "),
            targetClass: this.tClass ? this.tClass : "ml15",
            showup:true,
            animations:['zoom-in-up','fade-up','fade-right','fade-left','fade-up-left','fade-down-right','fade-down-left']
        }
    },
    mounted(){
      AOS.init();
        
    },
     methods:{
  },
  created(){
  }
}
</script>

<style >

.word {
  display: inline-block;
  line-height: 1em;
  font-weight: normal;
  font-size:30px;
background:-webkit-linear-gradient(#bc4e9c, #f80759);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
  
}
</style>