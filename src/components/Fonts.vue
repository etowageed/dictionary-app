<template>
    <div>
        <select name="fontSelector" id="fonts" v-model="selectedFont">
            <option value="Merriweather">Serif</option>
            <option value="Roboto">Sans-serif</option>
            <option value="Source Code Pro">Monospace</option>
        </select>
    </div>
</template>

<script>
export default {
    name: 'Fonts',

    inject: ['selectedFont'],

}

</script>

<style></style>