<template>
    <div class="text-center">
      <h1 class="ml16 font-barlow yellow--text">Instalacion de LAMPP Y IIS</h1>
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
        var textWrapper = document.querySelector('.ml16');
textWrapper.innerHTML = textWrapper.textContent.replace(/([^\x00-\x80]|\w)/g, "<span class='letter'>$&</span>");

this.$anime.timeline()
  .add({
    targets: '.ml16 .letter',
    translateY: [-100,0],
    easing: "easeOutExpo",
    duration: 1400,
    delay: function(el, i) {
      return 30 * i;
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

.ml16 {
  padding: 40px 0;
  font-weight: 800;
  font-size: 2em;
  text-transform: uppercase;
  letter-spacing: 0.5em;
  overflow: hidden;
}
.ml16 .letter {
  display: inline-block;
  line-height: 1em;
}
</style>