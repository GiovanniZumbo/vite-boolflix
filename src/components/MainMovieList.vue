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
    <h3>MAINCARDLIST</h3>

    <div class="cardlist">
        <MainMovieCard v-for="movie in store.movieList" :movie="movie" />

    </div>


</template>

<style scoped></style>