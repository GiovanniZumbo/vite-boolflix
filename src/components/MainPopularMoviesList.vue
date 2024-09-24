<script>
import axios from 'axios';

export default {
    data() {
        return {
            popularUrlApi:
                "https://api.themoviedb.org/3/movie/popular",
            popularMovies: '',
        }
    }
    ,

    methods: {
        getPopularList() {
            axios.get(this.popularUrlApi, {
                params: {
                    api_key: "c9c806bca4bbfddd92bba4b4d36d3a53",
                    language: "it-IT",
                }
            })
                .then(result => {
                    this.popularMovies = result.data.results;
                    console.log("POPULAR:", this.popularMovies);
                })
                .catch(function (error) {
                    console.log(error);
                })

        },

        mounted() {
            this.getPopularList();
        }
    }
}
</script>

<template>
    <h3 class="text-light">FILM POPOLARI ADESSO</h3>
</template>

<style scoped></style>