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

    <div class="cardlist">
        <MainSeriesCard v-for="series in store.seriesList" :series="series" />

    </div>

</template>

<style lang="scss" scoped>
@use "../styles/generics.scss" as *
</style>