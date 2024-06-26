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
  <div class="flex flex-col justify-between p-8">
    <Header class=" mb-20" />

    <!-- <Search class="w-3/4 md:w-1/3 mx-auto"></Search> -->



    <Search class="w-2/4 mx-auto" />



    <Footer />

  </div>


</template>


<style></style>
