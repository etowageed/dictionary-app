<template>
    <div>
        <select name="fontSelector" id="fonts" v-model="selectedFont"
            class="rounded bg-primary-bg text-primary-txt pl-1 py-1">
            <option value="Merriweather">Serif</option>
            <option value="Roboto">Sans-serif</option>
            <option value="Source Code Pro">Monospace</option>
        </select>
    </div>
</template>

<script>
export default {
    name: 'Fonts',

    data() {
        return {
            selectedFont: 'Source Code Pro',

        }
    },
    mounted() {
        this.emitFontProp();

    },

    updated() {
        this.emitFontProp();
    },
    methods: {
        emitFontProp() {
            this.$emit('font-event', this.selectedFont)
        }
    }
}

</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Merriweather+Sans:ital,wght@0,300..800;1,300..800&family=Roboto:ital,wght@0,100;0,300;0,400;0,500;0,700;0,900;1,100;1,300;1,400;1,500;1,700;1,900&family=Source+Code+Pro:ital,wght@0,200..900;1,200..900&display=swap');
</style>