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
    <div class="container">
        <MainMovieList />
        <MainSeriesList />
    </div>
</template>

<style lang="scss" scoped></style>