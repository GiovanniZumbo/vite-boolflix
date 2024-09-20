<script>
//Imported packages
import axios from 'axios';
//store
import { store } from '../store';

export default {
    data() {
        return {
            urlApi: "https://api.themoviedb.org/3/search/movie",
            movieList: ""
        }
    },

    methods: {
        //API call to find the requested movies
        getMoviesList() {
            axios.get(this.urlApi, {
                params: {
                    api_key: "c9c806bca4bbfddd92bba4b4d36d3a53",
                    query: store.userRequest,
                    language: "it-IT",
                }
            })
                .then(response => {
                    this.movieList = response.data.results;
                    console.log(this.movieList)
                })
        }

    }
}
</script>

<template>
    <h3>MAIN</h3>



</template>

<style scoped></style>