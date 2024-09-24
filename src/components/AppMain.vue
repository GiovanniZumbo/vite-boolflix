<script>


import { store } from '../store';
import MainMovieList from './MainMovieList.vue';
import MainPopularMoviesList from './MainPopularMoviesList.vue';
import MainSeriesList from './MainSeriesList.vue';


export default {
    data() {
        return {
            store
        }
    },

    components: {
        MainMovieList,
        MainSeriesList,
        MainPopularMoviesList

    }
}
</script>

<template>
    <div class="container">
        <div v-if="store.movieList && store.seriesList">
            <MainMovieList />
            <MainSeriesList />
        </div>
        <div v-else>
            <MainPopularMoviesList />
        </div>
    </div>
</template>

<style lang="scss" scoped></style>