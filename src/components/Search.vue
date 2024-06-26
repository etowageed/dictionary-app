<template>

    <div class="w-full md:w-2/4 my-20">


        <form @submit="submitForm">

            <!-- can also use @submit.prevent to stop the default behaviour  -->
            <div class="flex justify-between">
                <input type="text" placeholder="Type a word to search" v-model="search"
                    class="rounded-l-full h-16 w-full px-6 text-primary-txt font-semibold bg-bder-col focus:outline-none focus:ring-2 focus:ring-primary-col"
                    @keydown.enter="searchWord" required />
                <button class="bg-primary-col w-16 h-[65px] rounded-r-full inline-block p-2"><img
                        src="@/assets/searchicon.svg" alt="" class="w-9 h-9" @click="searchWord"></button>
            </div>
        </form>




        <!-- word content-->

        <div v-for="(entry, index)  in    searchedWord   " :key="index" class="mt-14 text-primary-txt">

            <h2 class="text-5xl font-bold text-primary-txt">{{ entry.word }}</h2>


            <!-- this allows only the first entry in the array of phonetic texts -->
            <div v-for="(phonetic, index) in entry.phonetics" :key="index">

                <p v-if="index === 0">{{ phonetic.text }}</p>

            </div>

            <!-- this allows only the first entry to have a soundClip audio -->
            <div v-if="index === 0" v-for="(soundClip, index) in  entry.phonetics" :key="index" class="mt-10">

                <audio v-if="index === 0" controls class="block mb-10">
                    <source v-bind:src="soundClip.audio" type="audio/mpeg">
                    Your browser does not support the audio element.
                </audio>
            </div>

            <!-- <div v-if="firstNonEmptySoundClip">
    <audio controls class="block mb-10">
        <source v-bind:src="firstNonEmptySoundClip.audio" type="audio/mpeg">
        Your browser does not support the audio element.
    </audio>
</div> -->









            <div v-for="(   meaning, index   ) in      entry.meanings    " :key="index.meaning">

                <br>
                <p class="font-bold italic">{{ meaning.partOfSpeech }}</p>
                <hr>
                <br>
                <p class="text-primary-txt opacity-75">Meaning</p>

                <br>

                <!-- meaning list  -->
                <div class="pl-10">
                    <li class="list-disc marker:text-primary-col"
                        v-for="(   wordMeaning, index   ) in    meaning.definitions   " :key="wordMeaning">

                        <!-- <li class="list-disc" v-for="wordMeaning in meaning.definitions" :key="wordMeaning"> -->

                        {{ wordMeaning.definition }}
                        <p class="italic opacity-75">{{ wordMeaning.example }}</p>
                        <br>
                    </li>
                    <br>
                </div>


                <!-- synonyms -->
                <p class="text-primary-txt opacity-75">Synonyms</p>
                <p v-for="   synonym    in    meaning.synonyms   ">{{ synonym }}, </p>
                <!-- <p>{{ meaning.synonyms }} </p> -->

                <br>

                <!-- antonyms -->
                <p class="text-primary-txt opacity-75">Antonyms</p>
                <span v-for="   antonym    in    meaning.antonyms   ">{{ antonym }}, </span>
            </div>



            <br>
            <p>Source</p>
            <a href="" v-for="   link    in    entry.sourceUrls   " target="_blank">{{ link }}</a>

        </div>


    </div>
</template>

<script>
import axios from 'axios';
// import { mdiPlayCircle } from 'vue-material-design-icons'

export default {
    name: 'Search',
    data() {
        return {
            search: '',
            errorMsg: '',
            searchedWord: '',
            // firstNonEmptySoundClip: null,
            // phonetics: [],
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
                    this.searchedWord = response.data,

                        this.phonetics = searchedWord.phonetics
                    // this.findFirstNonEmptySoundClip()


                })
                .catch((error) => {

                    this.errorMsg = 'Oops! there seems to be an error'
                    console.log(this.errorMsg)
                })

            this.search = ''
        },
        // findFirstNonEmptySoundClip() {
        //     this.firstNonEmptySoundClip = this.phonetics.find(soundClip => soundClip.audio && soundClip.audio.trim() !== '')
        // }
    }
}
</script>

<style scoped>
::placeholder {
    font-weight: normal;
    font-style: italic;
}
</style>