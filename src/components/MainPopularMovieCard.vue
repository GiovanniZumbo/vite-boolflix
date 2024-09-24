<script>
export default {
    data() {
        return {

        }
    },

    props: {
        popularMovie: {
            type: Object,
            Required: true
        }
    },

    computed: {
        languageClass() {


            switch (this.popularMovie.original_language) {
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
                    return `fi-${this.popularMovie.original_language}`;

            }
        },
        posterImage() {
            return `https://image.tmdb.org/t/p/w342${this.popularMovie.poster_path}`;
        },

        integerVote() {
            return Math.ceil(this.popularMovie.vote_average / 2);
        }
    }

}
</script>

<template>
    <div class="card position-relative top-0 start-0 w-100 h-100 bg-dark">
        <div class=" card-poster align-content-center">
            <img src="../assets/boolflix_logo_small.png" alt="" v-if="this.popularMovie.poster_path === null">
            <img :src="posterImage" class="card-img-top" alt="..." v-else>
        </div>
        <div class="card-body position-absolute top-0 start-0 text-light">
            <p class="title"><b>Titolo</b>: "{{ popularMovie.title }}" </p>
            <p class="og-title"><b>Titolo originale</b>: "{{ popularMovie.original_title }}</p>

            <p class="lang"><b>Lingua</b>: <span class="fi" :class="languageClass"> </span> </p>
            <p class="vote"><b>Voto</b>: <i class="fa-solid fa-star" v-for="n in integerVote"></i> <i
                    class="fa-regular fa-star" v-for="n in (5 - integerVote)"></i></p>
            <p class="overview text-truncate" v-text="popularMovie.overview ? popularMovie.overview : 'N/A'"></p>
        </div>
    </div>

</template>

<style scoped></style>