<template>
    <div >
       <h1 s class="ml15 text-center mt-5 font-ubuntu">
  <span tyle="font-size:50px" class="word">PORTAFOLIO</span>
  <span tyle="font-size:50px" class="word">GSW</span>
  <span tyle="font-size:50px" class="word">2019</span>
</h1>
    </div>
</template>

<script>
export default {
    props:['title'],
    data(){
        return{

        }
    },
    mounted(){
this.$anime.timeline()
  .add({
    targets: '.ml15 .word',
    scale: [14,1],
    opacity: [0,1],
    easing: "easeOutCirc",
    duration: 800,
    delay: function(el, i) {
      return 800 * i;
    }
  })
    }
}
</script>

<style>

@media(max-width: 600px) {
 .font-julius-sans-one{
   font-family:"roboto";
 }
}

</style>