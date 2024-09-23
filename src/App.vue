<script>
// Imported Components
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';
//axios
import axios from 'axios';
//store
import { store } from './store';

export default {
  data() {
    return {
      urlApi: "https://api.themoviedb.org/3/search/movie",
      store
    }
  },

  methods: {

    //API call to find the requested movies
    getMoviesList(requestquery) {

      console.log(requestquery);

      axios.get(this.urlApi, {
        params: {
          api_key: "c9c806bca4bbfddd92bba4b4d36d3a53",
          query: requestquery,
          language: "it-IT",
        }
      })
        .then(response => {
          this.store.movieList = response.data.results;
        })
    }

  },

  components: {
    AppHeader,
    AppMain
  }
}
</script>

<template>

  <AppHeader @call-for-movies="getMoviesList" />
  <AppMain />
</template>

<style lang="scss">
@use "bootstrap/scss/bootstrap.scss" as *;
</style>