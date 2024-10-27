<script>
import Search from './components/Search.vue'
import Header from './components/Header.vue'
import Footer from './components/Footer.vue'
import Toggle from './components/Toggle.vue'
import Fonts from './components/Fonts.vue'


export default {
  name: 'App',
  components: {
    Search, Header, Footer, Toggle, Fonts,
  },

  data() {
    return {
      isDarkBg: false, // default theme is white so darkbg is false
      fontSelecta: '',
    };
  },

  provide() {
    return {
      toggleBtn: this.toggleDarkBg,
    }
  },

  methods: {
    toggleDarkBg() {
      this.isDarkBg = !this.isDarkBg;
    },

    handleEmittedFontProp(payload) {
      console.log("this is", payload)
      this.fontSelecta = payload;
    }
  }
}
</script>


<template>
  <div v-bind:style="{ fontFamily: fontSelecta }"
    class="flex flex-col justify-between p-8 text-primary-txt min-h-screen"
    v-bind:class="{ dark: isDarkBg, light: !isDarkBg }">

    <Header class=" mb-20" @font-event="handleEmittedFontProp" />

    <Search class="w-2/4 mx-auto" />



    <Footer />

  </div>


</template>


<style>
.light {
  background-color: white;
  color: #3d3d3d;
}

.dark {
  background-color: #121212;
  color: white;
}
</style>
