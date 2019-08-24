<template>
  <v-card
    class="mx-auto"
    color="#0B0014"
    dark
    flat
    max-width="900"
  >

    <v-card-text class="font-darker-grotesque">
      <v-card-title><slot></slot></v-card-title>
      <h1 class="ml2 text-justify" v-if="fancyAnimation" :class="this.classAdd" v-html="textCard"></h1>
      <h1 class="ml2 text-justify" v-else :data-aos="animations[Math.ceil((Math.random()*animations.length))]" v-html="textCard"></h1>
    <v-card-actions>
      <v-list-item class="grow">
        

        <v-row
          align="center"
          justify="end"
          v-if="links.length>0"
        >
          <v-chip v-for="(linked,index) in links" :key="index" class="linkedclass animated fadeInUp" :color="linked.color ? linked.color: 'primary'">
              <v-icon class="mr-1" >insert_link</v-icon>
          <a :href="linked.to" target="_blank" style="color:white; text-decoration:none;" class="subheading mr-2">{{linked.text}}</a>
          <span class="mr-1"></span>
          </v-chip>
          <br>
        </v-row>
      </v-list-item>
    </v-card-actions>
    </v-card-text>

  </v-card>
</template>

<script>
export default {
    props:['textCard','linksCard','classAdd','fancy'],
    data(){
        return{
            links:this.linksCard ? this.linksCard : [],
            fancyAnimation: this.fancy,
            animations:['zoom-in-up','fade-up','fade-right','fade-left','fade-up-left','fade-down-right','fade-down-left']
        }
    },
    mounted(){
        // Wrap every letter in a span


if(this.fancyAnimation){
  var textWrapper = document.querySelector('.'+this.classAdd);
textWrapper.innerHTML = textWrapper.textContent.replace(/([^\x00-\x80]|\w)/g, "<span class='lettercard'>$&</span>");
  this.$anime.timeline({delay:1000})
  .add({
    targets: '.ml2 .lettercard',
    scale: [4,1],
    opacity: [0,1],
    translateZ: 0,
    easing: "easeOutExpo",
    duration: 950,
    delay: function(el, i) {
      return 10*i;
    }
  })
}
    }
}
</script>

<style>

</style>