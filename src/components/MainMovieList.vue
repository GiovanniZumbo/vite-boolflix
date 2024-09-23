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

    <h2>MOVIES </h2>
    <div class="cardlist d-flex row row-cols-5 g-3">
        <div class="col" v-for="movie in store.movieList">
            <MainMovieCard :movie="movie" />
        </div>
    </div>


</template>

<style lang="scss" scoped>
@use "../styles/generics.scss" as *;

h2 {
    color: white;
}
</style>