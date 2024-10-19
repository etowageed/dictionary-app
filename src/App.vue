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
      selectedFont: 'Source Code Pro',
    };
  },

  provide() {
    return {
      toggleBtn: this.toggleDarkBg,
      selectedFont: () => this.selectedFont
    }
  },

  methods: {
    toggleDarkBg() {
      this.isDarkBg = !this.isDarkBg;

    }
  }
}
</script>


<template>
  <div v-bind:style="{ fontFamily: selectedFont }"
    class="flex flex-col justify-between p-8 text-primary-txt min-h-screen"
    v-bind:class="{ dark: isDarkBg, light: !isDarkBg }">

    <Header class=" mb-20" />

    <select name="fontSelector" id="fonts" v-model="selectedFont">
      <option value="Merriweather">Serif</option>
      <option value="Roboto">Sans-serif</option>
      <option value="Source Code Pro">Monospace</option>
    </select>

    <Search class="w-2/4 mx-auto" />



    <Footer />

  </div>


</template>




<style>
/* @import url('https://fonts.googleapis.com/css2?family=Roboto:ital,wght@0,100;0,300;0,400;0,500;0,700;0,900;1,100;1,300;1,400;1,500;1,700;1,900&display=swap'); */
/* @import url('https://fonts.googleapis.com/css2?family=Merriweather+Sans:ital,wght@0,300..800;1,300..800&family=Roboto:ital,wght@0,100;0,300;0,400;0,500;0,700;0,900;1,100;1,300;1,400;1,500;1,700;1,900&display=swap'); */
@import url('https://fonts.googleapis.com/css2?family=Merriweather+Sans:ital,wght@0,300..800;1,300..800&family=Roboto:ital,wght@0,100;0,300;0,400;0,500;0,700;0,900;1,100;1,300;1,400;1,500;1,700;1,900&family=Source+Code+Pro:ital,wght@0,200..900;1,200..900&display=swap');

.sourcky {
  font-family: 'Source Code Pro', monospace;
}

.light {
  background-color: white;
  color: #3d3d3d;
}

.dark {
  background-color: #121212;
  color: white;
}
</style>
