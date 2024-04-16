<template>

    <form @submit="submitForm">
        <div class="flex justify-between">
            <input type="text" placeholder="Type a word to search" v-model="search"
                class="rounded-l-full h-16 w-full px-6 text-primary-txt font-semibold bg-bder-col focus:outline-none focus:ring-2 focus:ring-primary-col" />
            <button class="bg-primary-col w-16 h-[65px] rounded-r-full inline-block p-2"><img
                    src="@/assets/searchicon.svg" alt="" class="w-9 h-9" @click="searchWord"></button>
        </div>
    </form>
</template>

<script>
import axios from 'axios';

export default {
    name: 'Search',
    data() {
        return {
            search: '',
            errorMsg: 'Oops!!'
        }
    },
    methods: {
        submitForm(event) {
            event.preventDefault()
        },

        searchWord() {
            axios.get(`https://api.dictionaryapi.dev/api/v2/entries/en/${this.search}`)
                .then((response) => {
                    console.log(response.data)
                })
                .catch((error) => {
                    console.log(this.errorMsg)

                })
        }
    }
}
</script>

<style scoped>
::placeholder {
    font-weight: normal;
    font-style: italic;
}
</style>