<template>

    <form @submit="submitForm">

        <!-- can also use @submit.prevent to stop the default behaviour  -->
        <div class="flex justify-between">
            <input type="text" placeholder="Type a word to search" v-model="search"
                class="rounded-l-full h-16 w-full px-6 text-primary-txt font-semibold bg-bder-col focus:outline-none focus:ring-2 focus:ring-primary-col"
                @keydown.enter="searchWord" />
            <button class="bg-primary-col w-16 h-[65px] rounded-r-full inline-block p-2"><img
                    src="@/assets/searchicon.svg" alt="" class="w-9 h-9" @click="searchWord"></button>

        </div>
    </form>
    <!-- word content-->

    <div v-for="entry in focusWord" :key="index" class="mt-14">



        <p class="text-5xl font-bold text-primary-txt">{{ entry.word }}</p>
        <p>{{ entry.phonetic }}</p>

        <span v-for="sound in entry.phonetics">{{ sound.audio }}</span>

        <div v-for="(meaning, index) in   entry.meanings " :key="index.meaning">
            <br>
            <p class="font-bold italic">{{ meaning.partOfSpeech }}</p>
            <hr>
            <br>
            <p class="text-primary-txt opacity-75">Meaning</p>

            <br>

            <!-- meaning list  -->
            <div class="pl-10">
                <li class="list-disc" v-for="(wordMeaning, index) in meaning.definitions" :key="wordMeaning">

                    <!-- <li class="list-disc" v-for="wordMeaning in meaning.definitions" :key="wordMeaning"> -->

                    {{ wordMeaning.definition }}
                    <p class="italic">{{ wordMeaning.example }}</p>
                    <br>
                </li>
                <br>
            </div>


            <!-- synonyms -->
            <p class="text-primary-txt opacity-75">Synonyms</p>
            <p v-for="synonym in meaning.synonyms">{{ synonym }}, </p>
            <!-- <p>{{ meaning.synonyms }} </p> -->

            <br>

            <!-- antonyms -->
            <p class="text-primary-txt opacity-75">Antonyms</p>
            <span v-for="antonym in meaning.antonyms">{{ antonym }}, </span>
        </div>



        <br>
        <p>Source</p>
        <a href="" v-for="link in entry.sourceUrls" target="_blank">{{ link }}</a>

    </div>

</template>

<script>
import axios from 'axios';

export default {
    name: 'Search',
    data() {
        return {
            search: '',
            errorMsg: '',
            focusWord: '',

        }
    },
    methods: {
        submitForm(event) {
            event.preventDefault();

        },

        searchWord() {
            axios.get(`https://api.dictionaryapi.dev/api/v2/entries/en/${this.search}`)
                .then((response) => {
                    console.log(response.data)
                    this.focusWord = response.data


                })
                .catch((error) => {

                    this.errorMsg = 'Oops! there seems to be an error'
                    console.log(this.errorMsg)
                })

            this.search = ''
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