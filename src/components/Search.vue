<template>

    <form @submit="submitForm">

        <!-- can also use @submit.prevent to stop the default behaviour  -->

        <div class="flex justify-between border-4 border-t-primary-col">
            <input type="text" placeholder="Type a word to search" v-model="search"
                class="rounded-l-full h-16 w-full px-6 text-primary-txt font-semibold bg-bder-col focus:outline-none focus:ring-2 focus:ring-primary-col"
                @keydown.enter="searchWord" />

            <button class="bg-primary-col w-16 h-[65px] rounded-r-full inline-block p-2"><img
                    src="@/assets/searchicon.svg" alt="" class="w-9 h-9" @click="searchWord"></button>

        </div>
    </form>
    <!-- <Wordcontent /> -->

</template>

<script>
// import Wordcontent from "./components/Wordcontent.vue"

export default {
    name: 'Search',
    // components: { Wordcontent, },
    data() {

    }

}
</script>

<style scoped>
::placeholder {
    font-weight: normal;
    font-style: italic;
}
</style>