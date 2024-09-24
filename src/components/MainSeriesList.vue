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
        MainSeriesCard,
    },

}
</script>

<template>
    <div v-show="store.seriesList">
        <h3>SERIES</h3>

        <div class="cardlist d-flex row row-cols-5 g-3">
            <div class="col" v-for="series in store.seriesList">
                <MainSeriesCard :series="series" />
            </div>

        </div>
    </div>
</template>

<style lang="scss" scoped>
@use "../styles/generics.scss" as *;

h3 {
    color: white;
}
</style>