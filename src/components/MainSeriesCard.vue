<script>
export default {
    data() {
        return {

        }
    },

    props: {
        series: {
            type: Object,
            Required: true
        }
    },

    computed: {
        languageClass() {


            switch (this.series.original_language) {
                case "en":
                    return "fi-gb";
                case "ja":
                    return "fi-jp";
                case "ko":
                    return "fi-kr";
                case "zh":
                    return "fi-cn";
                case "da":
                    return "fi-dk";
                case "hi", "fa":
                    return "fi-xx"

                default:
                    return `fi-${this.series.original_language}`;

            }
        },

        posterImage() {
            return `https://image.tmdb.org/t/p/w342${this.series.poster_path}`;
        },

        integerVote() {
            return Math.ceil(this.series.vote_average / 2);
        }
    }




}
</script>

<template>

    <div class="card position-relative top-0 start-0">
        <div class=" card-poster">
            <img :src="posterImage" class="card-img-top" alt="...">
        </div>
        <div class="card-body position-absolute top-0 start-0">
            <p class="title">Titolo: "{{ series.name }}" </p>
            <p class="og-title">Titolo originale: "{{ series.original_name }}</p>

            <p class="lang">Lingua: <span class="fi" :class="languageClass"> </span> </p>
            <p class="vote">Voto: <i class="fa-solid fa-star" v-for="n in integerVote"></i></p>
            <p class="overview">{{ series.overview }}</p>
        </div>
    </div>

</template>

<style lang="scss">
@use "../styles/generics.scss" as *;

.overview {
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
}

.fi {
    box-shadow: 0 0 10px gray;
}
</style>