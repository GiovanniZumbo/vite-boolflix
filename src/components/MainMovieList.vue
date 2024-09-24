<script>

//store
import { store } from '../store';

//components
import MainMovieCard from './MainMovieCard.vue';

export default {
    data() {
        return {
            store,
        }
    },

    components: {
        MainMovieCard
    },

}
</script>

<template>

    <h3 class="text-light ms-2 mb-4">MOVIES</h3>

    <div v-if="store.movieList.length > 0">
        <div class="cardlist d-flex row row-cols-5 g-3 mb-5">
            <div class="col" v-for="movie in store.movieList">
                <MainMovieCard :movie="movie" />
            </div>
        </div>
    </div>

    <div v-else-if="store.movieList.length === 0">
        <p class=" text-light">Nessun risultato trovato.</p>
    </div>
</template>

<style lang="scss">
@use "../styles/generics.scss" as *;

h3 {
    color: white;
}
</style>