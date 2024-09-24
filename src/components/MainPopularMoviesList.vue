<script>
//store
import { store } from '../store';
//components
import MainPopularMovieCard from './MainPopularMovieCard.vue';

export default {
    data() {
        return {
            store,

        }
    }
    ,
    components: {
        MainPopularMovieCard
    },

}
</script>

<template>

    <h3 class="text-light ms-2 mb-4">FILM POPOLARI ADESSO</h3>

    <div class="cardlist d-flex row row-cols-5 g-3 mb-5">
        <div class="col" v-for="popularMovie in store.popularMovies">
            <MainPopularMovieCard :popularMovie="popularMovie" />
        </div>
    </div>


</template>

<style scoped></style>