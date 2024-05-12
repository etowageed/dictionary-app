<template>
    <div v-for="entry in focusWord" :key="index">



        <p class="text-5xl font-bold text-primary-txt">{{ entry.word }}</p>
        <p>{{ entry.phonetic }}</p>

        <span v-for="sound in entry.phonetics">{{ sound.audio }}</span>

        <div v-for="(meaning, index) in   entry.meanings " :key="index.meaning">
            <p class="font-bold italic">{{ meaning.partOfSpeech }}</p>
            <hr>

            <p class="text-primary-txt opacity-75">Meaning</p>

            <li class="list-disc" v-for="(wordMeaning, index) in meaning.definitions" :key="wordMeaning">

                <!-- <li class="list-disc" v-for="wordMeaning in meaning.definitions" :key="wordMeaning"> -->

                {{ wordMeaning.definition }}
                <p class="italic">{{ wordMeaning.example }}</p>
            </li>




            <p class="text-primary-txt opacity-75">Synonyms</p>

            <span v-for="synonym in meaning.synonyms">{{ synonym }}, </span>

            <p class="text-primary-txt opacity-75">Antonyms</p>
            <span v-for="antonym in meaning.antonyms">{{ antonym }}, </span>
        </div>
        <hr>
        <p>Source</p>
        <a href="" v-for="link in entry.sourceUrls" target="_blank">{{ link }}</a>

    </div>

</template>

<script>

import axios from 'axios';

export default {
    name: 'WordContent',
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
                    this.focusWord = response.data
                    console.log(response.data)
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

<style lang="scss" scoped></style>