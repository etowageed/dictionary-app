<template>

    <form action="">
        <div class="flex justify-between">
            <input type="text" placeholder="Type a word to search" v-model="search"
                class="rounded-l-full h-16 w-full px-6 text-primary-txt font-semibold bg-bder-col focus:outline-none focus:ring-2 focus:ring-primary-col" />
            <button class="bg-primary-col w-16 h-[65px] rounded-r-full inline-block p-2"><img
                    src="@/assets/searchicon.svg" alt="" class="w-9 h-9"></button>
        </div>
    </form>

</template>

<script>
export default {
    name: 'Search',
    data() {
        return {
            search: '',
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