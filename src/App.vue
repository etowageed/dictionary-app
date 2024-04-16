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

    }
  }
}
</script>

<template>
  <div class="h-screen flex flex-col justify-between">
    <Header class=" p-8" />

    <Search class="w-3/4 md:w-1/3 mx-auto"></Search>

    <Footer class="p-8" />

  </div>


</template>

<style></style>
