<script>
import axios from 'axios';
export default {
    data() {
        return {
            castMembers: '',
        }
    },


    props: {
        movie: {
            type: Object,
            Required: true
        }
    },

    computed: {
        languageClass() {


            switch (this.movie.original_language) {
                case "en":
                    return "fi-gb";
                case "ja":
                    return "fi-jp";
                case "ko":
                    return "fi-kr";
                case "zh":
                    return "fi-cn";
                case "hi":
                    return "fi-in";
                case "fa":
                    return "fi-xx";

                default:
                    return `fi-${this.movie.original_language}`;

            }
        },

        posterImage() {
            return `https://image.tmdb.org/t/p/w342${this.movie.poster_path}`;
        },

        integerVote() {
            return Math.ceil(this.movie.vote_average / 2);
        },

        castUrlApi() {
            return `https://api.themoviedb.org/3/movie/${this.movie.id}/credits`;
        }
    },

    mounted() {
        if (this.movie) {
            this.getCast();
        }
    },

    methods: {

        //API call to get the cast members
        getCast() {
            axios.get(this.castUrlApi, {
                params: {
                    api_key: "c9c806bca4bbfddd92bba4b4d36d3a53",
                    language: "it-IT",
                }
            })
                .then(result => {
                    this.castMembers = result.data.cast;
                })
                .catch(function (error) {
                    console.log(error);
                })

        }
    }
}
</script>

<template>

    <div class="card position-relative top-0 start-0 w-100 h-100 bg-dark">
        <div class=" card-poster align-content-center">
            <img src="../assets/boolflix_logo_small.png" alt="" v-if="this.movie.poster_path === null">
            <img :src="posterImage" class="card-img-top" alt="..." v-else>
        </div>
        <div class="card-body position-absolute top-0 start-0 text-light">
            <p class="title"><b>Titolo</b>: "{{ movie.title }}" </p>
            <p class="og-title"><b>Titolo originale</b>: "{{ movie.original_title }}</p>

            <p class="lang"><b>Lingua</b>: <span class="fi" :class="languageClass"> </span> </p>
            <p class="cast"><b>Cast</b>: <span v-for="(member, i) in castMembers.slice(0, 5)" :key="i">{{ member.name
                    }}, </span>...</p>
            <p class="vote"><b>Voto</b> : <i class="fa-solid fa-star" v-for="n in integerVote"></i><i
                    class="fa-regular fa-star" v-for="n in (5 - integerVote)"></i></p>
            <div>
                <p class="overview" v-text="movie.overview ? movie.overview : 'N/A'">
                </p>
            </div>
        </div>
    </div>
</template>

<style lang="scss">
@use "../styles/generics.scss" as *;

.fa-star {
    color: gold;
}

.card {
    height: 523px;
    border-radius: 25px;

    transition: 0.2s ease-in-out;
    transform-style: preserve-3d;
    backface-visibility: hidden;
    transition: 1s ease-in-out;
    cursor: pointer;

    &:hover {
        transform: rotateY(0.5turn);
    }
}

.card-poster,
.card-body {
    width: 100%;
    height: 100%;
    backface-visibility: hidden;
    transition: 1s ease-in-out;
}

.card-body {
    transform: rotateY(0.5turn);
    background-color: black;
    overflow: scroll;

    &::-webkit-scrollbar {
        display: none;
    }
}



.fi {
    box-shadow: 0 0 10px gray;
}
</style>