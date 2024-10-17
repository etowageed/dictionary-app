<script>
import Search from './components/Search.vue'
import Header from './components/Header.vue'
import Footer from './components/Footer.vue'

export default {
  name: 'App',
  components: {
    Search, Header, Footer,
  },

  data() {
    return {
      isDarkBg: 'false' // default theme is white so darkbg is false

    };
  },
  methods: {
    toggleDarkBg() {
      this.isDarkBg = !this.isDarkBg;

    }
  }
}
</script>

<template>
  <div class="flex flex-col justify-between p-8 text-primary-txt min-h-screen"
    v-bind:class="{ dark: isDarkBg, light: !isDarkBg }">

    <Header class=" mb-20" />

    <!-- <Search class="w-3/4 md:w-1/3 mx-auto"></Search> -->

    <button @click="toggleDarkBg">toggle darkmode</button>

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
