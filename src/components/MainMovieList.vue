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
    <h3>MAINMOVIESCARDSLIST</h3>

    <ul class="cardlist" v-for="movie in store.movieList">
        <li>
            <MainMovieCard :movie="movie" />
        </li>
    </ul>


</template>

<style lang="scss" scoped>
@use "../styles/generics.scss" as *
</style>