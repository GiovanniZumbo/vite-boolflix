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
      moviesUrlApi: "https://api.themoviedb.org/3/search/movie",
      seriesUrlApi: "https://api.themoviedb.org/3/search/tv",
      popularUrlApi: "https://api.themoviedb.org/3/movie/popular",
      moviesGenresUrl: "https://api.themoviedb.org/3/genre/movie/list",
      store
    }
  },

  methods: {

    getMoviesList(requestquery) {

      console.log(requestquery);

      //API call to get the requested movies
      axios.get(this.moviesUrlApi, {
        params: {
          api_key: "c9c806bca4bbfddd92bba4b4d36d3a53",
          query: requestquery,
          language: "it-IT",
        }
      })
        .then(response => {
          this.store.movieList = response.data.results;
          console.log("MOVIES:", this.store.movieList)
        })
        .catch(function (error) {
          console.log(error);
        })

      //API call to get the requested series

      axios.get(this.seriesUrlApi, {
        params: {
          api_key: "c9c806bca4bbfddd92bba4b4d36d3a53",
          query: requestquery,
          language: "it-IT",
        }
      })
        .then(result => {
          this.store.seriesList = result.data.results;
          console.log("SERIES:", this.store.seriesList);
        })
        .catch(function (error) {
          console.log(error);
        })
    },

    //API call to get popular movies list

    getPopularList() {
      axios.get(this.popularUrlApi, {
        params: {
          api_key: "c9c806bca4bbfddd92bba4b4d36d3a53",
          language: "it-IT",
        }
      })
        .then(result => {
          this.store.popularMovies = result.data.results;
          console.log("POPULAR:", this.store.popularMovies);
        })
        .catch(function (error) {
          console.log(error);
        })
    }

    //call to get movies genres
    // getMoviesGenres() {
    //   axios.get(this.moviesGenresUrl, {
    //     params: {
    //       api_key: "c9c806bca4bbfddd92bba4b4d36d3a53",
    //       language: "it-IT",
    //     }
    //   })
    //     .then(result => {
    //       this.store.moviesGenres = result.data.genres;
    //       console.log("Movies Genres:", this.store.moviesGenres);
    //     })
    //     .catch(function (error) {
    //       console.log(error);
    //     })
    // },

  },

  components: {
    AppHeader,
    AppMain
  },

  created() {
    this.getPopularList();
    // this.getMoviesGenres();
  }
}
</script>

<template>

  <body>

    <AppHeader @call-database="getMoviesList" />
    <AppMain />

  </body>
</template>

<style lang="scss" scoped>
@use "./styles/generics.scss" as *;
@use "./styles/variables.scss" as *;

body {
  min-height: 100vh;
  position: relative;
  background-color: #1B1B1B;
  ;
}
</style>