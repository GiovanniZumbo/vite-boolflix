<script>


import MainMovieList from './MainMovieList.vue';
import MainSeriesList from './MainSeriesList.vue';


export default {
    data() {
        return {

        }
    },

    components: {
        MainMovieList,
        MainSeriesList
    }
}
</script>

<template>
    <h2>-MAIN-</h2>
    <MainMovieList />
    <MainSeriesList />
</template>

<style scoped></style>