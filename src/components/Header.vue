<template>
    <div class="border flex justify-between">

        <a href="#" class="text-primary-col font-semibold text-base">Dictionary App</a>
        <div class=" md:w-1/5 py-1 flex justify-between">

            <Fonts class="inline" />
            <Toggle class="inline" />
        </div>


    </div>
</template>

<script>
import Toggle from './Toggle.vue';
import Fonts from './Fonts.vue';
export default {
    name: 'Header',

    components: {
        Toggle, Fonts,

    }
}
</script>

<style lang="scss" scoped></style>