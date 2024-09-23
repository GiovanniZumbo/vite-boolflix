<script>

//store
import { store } from '../store';

//components
import MainSeriesCard from './MainSeriesCard.vue';

export default {
    data() {
        return {
            store,
        }
    },

    components: {
        MainSeriesCard
    },

}
</script>

<template>
    <h3>MAINSERIESCARDSLIST</h3>

    <ul class="cardlist">
        <li v-for="series in store.seriesList">
            <MainSeriesCard :series="series" />
        </li>

    </ul>

</template>

<style lang="scss" scoped>
@use "../styles/generics.scss" as *;
</style>