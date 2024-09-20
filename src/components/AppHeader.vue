<script>
//Store
import { store } from '../store'
//axios
import axios from 'axios';

export default {
    data() {
        return {
            store,
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
    <h1>HEADER</h1>
    <div class="input-group mb-3 w-25">
        <input type="text" class="form-control" placeholder="Search..." v-model="store.userRequest"
            @keyup.enter="getMoviesList()">
        <button class="btn btn-outline-secondary" type="button" id="button-addon2" @click="getMoviesList()">Search
        </button>
    </div>

    <div class="cardlist">
        CARDLIST
        <div class="card" v-for="movie in movieList">
            <p class="title">Titolo: "{{ movie.title }}" </p>
            <p class="og-title">Titolo originale: "{{ movie.original_title }}</p>
            <p class="lang">Lingua: {{ movie.original_language }}</p>
            <p class="vote">Voto: {{ movie.vote_average }}</p>
        </div>
    </div>
</template>

<style scoped></style>