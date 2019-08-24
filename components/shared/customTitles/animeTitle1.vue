<template>
    <div >
        <h1 class="ml11 ">
  <span class="text-wrapper ">
    <span class="line line1"></span>
    <span class="letters font-julius-sans-one">  {{title}}</span>
  </span>
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
        // Wrap every letter in a span
var textWrapper = document.querySelector('.ml11 .letters');
textWrapper.innerHTML = textWrapper.textContent.replace(/([^\x00-\x80]|\w)/g, "<span class='letter'>$&</span>");

this.$anime.timeline()
  .add({
    targets: '.ml11 .line',
    scaleY: [0,1],
    opacity: [0.5,1],
    easing: "easeOutExpo",
    duration: 700
  })
  .add({
    targets: '.ml11 .line',
    translateX: [0, document.querySelector('.ml11 .letters').getBoundingClientRect().width + 10],
    easing: "easeOutExpo",
    duration: 700,
    delay: 100
  })
  .add({
    targets: '.ml11 .letter',
    opacity: [0,1],
    easing: "easeOutExpo",
    duration: 600,
    delay: function(el, i) {
      return 34 * (i+1)
    }
  })
  .add({
    targets: '.ml11 .line',
    translateX: [document.querySelector('.ml11 .letters').getBoundingClientRect().width + 10,0],
    easing: "easeOutExpo",
    duration: 700,
    delay: 100
  })
  .add({
    targets: '.ml11 .line',
    scaleY: [1,0],
    opacity: [0.5,1],
    easing: "easeOutExpo",
    duration: 700
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