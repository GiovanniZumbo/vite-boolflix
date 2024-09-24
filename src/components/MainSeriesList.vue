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
    <h3 class="text-light ms-2 mb-4">SERIES</h3>

    <div v-if="store.seriesList.length > 0">
        <div class="cardlist d-flex row row-cols-5 g-3">
            <div class="col" v-for="series in store.seriesList">
                <MainSeriesCard :series="series" />
            </div>
        </div>
    </div>
    <div v-else-if="store.seriesList.length === 0">
        <p class="text-light">Nessun risultato trovato.</p>
    </div>
</template>

<style lang="scss" scoped>
@use "../styles/generics.scss" as *;
</style>