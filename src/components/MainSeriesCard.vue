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
                case "hi", "fa":
                    return "fi-xx"

                default:
                    return `fi-${this.series.original_language}`;

            }
        },

        posterImage() {
            return `https://image.tmdb.org/t/p/w154${this.series.poster_path}`;
        }
    }


}
</script>

<template>
    <h4>MAIN SERIES CARD</h4>

    <div class="card">
        <img :src="posterImage" alt="">
        <p class="title">Titolo: "{{ series.name }}" </p>
        <p class="og-title">Titolo originale: "{{ series.original_name }}</p>

        <p class="lang">Lingua: <span class="fi" :class="languageClass"> </span> </p>
        <p class=" vote">Voto: {{ series.vote_average }}</p>
    </div>
</template>

<style lang="scss" scoped>
@use "../styles/generics.scss" as *;

.card {
    width: 300px;
}

.fi {
    box-shadow: 0 0 10px gray;
}
</style>