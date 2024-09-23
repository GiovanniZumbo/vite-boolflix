<script>
export default {
    data() {
        return {

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
                case "hi", "fa":
                    return "fi-xx"

                default:
                    return `fi-${this.movie.original_language}`;

            }
        },

        posterImage() {
            return `https://image.tmdb.org/t/p/w154${this.movie.poster_path}`;
        },

        integerVote() {
            return Math.ceil(this.movie.vote_average / 2);
        }
    },
}
</script>

<template>
    <h4>MAIN MOVIE CARD</h4>

    <div class="card">
        <img :src="posterImage" alt="">

        <p class="title">Titolo: "{{ movie.title }}" </p>
        <p class="og-title">Titolo originale: "{{ movie.original_title }}</p>

        <p class="lang">Lingua: <span class="fi" :class="languageClass"> </span> </p>
        <p class="vote">Voto: <i class="fa-solid fa-star" v-for="n in integerVote"></i></p>
    </div>
</template>

<style lang="scss">
@use "../styles/generics.scss" as *;

.fa-star {
    color: gold;
}

.card {
    width: 300px;
}

.fi {
    box-shadow: 0 0 10px gray;
}
</style>