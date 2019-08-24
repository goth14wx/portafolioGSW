<template>
  <v-app  :class="{'backgroundColor':true}">
    <v-navigation-drawer
      v-model="drawer"
      :mini-variant="miniVariant"
      fixed
      app
      :class="{'backgroundColor':true}"
    >
      <v-list  dense
          rounded
          v-for="(items,index) in drawerItems"
          :key="'drawer'+index"
          >
          
          <v-list-item-title  width="100%" style="font-size:25px;" class="font-monoton">
            <span v-if="!miniVariant">{{items.title}}</span>
            <div v-else  class="text-center letter">{{items.title.substr(0,1)}}</div>
            <v-row align="center" justify="center">
    <!--<v-img
      v-if="miniVariant"
      :src="items.icon"
      aspect-ratio="1"
      max-width="50px"
      max-height="50px"
    ></v-img>-->

  </v-row>
          </v-list-item-title>
          <v-divider
          light
        horizontal
      ></v-divider>
      <br>
        <v-list-item
          v-for="(item, i) in items.items"
          :key="i"
          :to="item.to"
          router
          exact
          class="animated fadeInUp"
        >
          <v-list-item-action>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title class="text-truncate font-barlow" v-text="item.title" />
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <v-app-bar
      :clipped-left="clipped"
      fixed
      app
        :class="{'backgroundColor':true}"
    >
      <v-app-bar-nav-icon class="d-lg-none d-xl-flex" @click.stop="drawer = !drawer" />
      <v-btn
        icon
        class="d-xs-none d-xs-flex"
        @click.stop="miniVariant = !miniVariant"
      >
        <v-icon>mdi-{{ `chevron-${miniVariant ? 'right' : 'left'}` }}</v-icon>
      </v-btn>
      &nbsp&nbsp
      <v-toolbar-title class="font-poiret-one "> <nuxt-link style="text-decoration:none !important; color:white;" :to="{path:'/'}">{{title}}</nuxt-link> </v-toolbar-title>
      <v-spacer />
    </v-app-bar>
    <v-content  >
      <v-container fluid grid-list-md>
        <nuxt />
      </v-container>
    </v-content>
    <v-navigation-drawer
      v-model="rightDrawer"
      :right="right"
      temporary
      fixed
        :class="{'backgroundColor':true}"
    >
      <v-list>
        
        <v-list-item @click.native="right = !right">
          <v-list-item-action>
            <v-icon light>
              mdi-repeat
            </v-icon>
          </v-list-item-action>
          <v-list-item-title>Switch drawer (click me)</v-list-item-title>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
  </v-app>
</template>

<script>
export default {
  data () {
    return {
      clipped: false,
      drawer: true,
      fixed: false,
      drawerItems:[
        {
          title:"XAMPP",
          icon:"./drawerIcons/XAMPP-icon.png",
          items: [
        {
          icon: 'desktop_windows',
          title: 'Preparando Todo',
          to: '/linux/setup'
        },
        {
          icon: 'http',
          title: 'Instalando Apache',
          to: '/linux/apache'
        },
        {
          icon: 'storage',
          title: 'Instalando Mysql',
          to: '/linux/mysql'
        },
        {
          icon: 'dns',
          title: 'Instalando PHP',
          to: '/linux/php'
        },
        
        {
          icon: 'cloud_done',
          title: 'Virtualhost',
          to: '/linux/virtualhost'
        }
      ],
        },
        {
          title:"WINDOWS",
          icon:"./drawerIcons/WINDOWS-icon.png",
          items: [
        {
          icon: 'laptop_windows',
          title: 'Preparando Todo',
          to: '/windows/setup'
        }
        
      ],
        }
      ],
      miniVariant: false,
      right: true,
      rightDrawer: false,
      title: 'Portafolio GSW 2019'
    }
  },
  mounted(){
    
  }
}
</script>

<style scoped>
.letter {
    line-height: 1em;
    font-size: 35px;
    font-weight: bold;
    background:-webkit-linear-gradient(#ee0979, #ff6a00);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
  }
</style>