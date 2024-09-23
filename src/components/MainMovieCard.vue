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
                    return "fi-cn"
                case "hi", "fa":
                    return "fi-xx"

                default:
                    return `fi-${this.movie.original_language}`;

            }
        }
    },
}
</script>

<template>
    <h4>MAIN MOVIE CARD</h4>
    CARDLIST
    <div class="card">
        <p class="title">Titolo: "{{ movie.title }}" </p>
        <p class="og-title">Titolo originale: "{{ movie.original_title }}</p>

        <p class="lang">Lingua: <span class="fi" :class="languageClass"> </span> </p>
        <p class=" vote">Voto: {{ movie.vote_average }}</p>
    </div>
</template>

<style lang="scss" scoped>
@use "../styles/generics.scss" as *;

.fi {
    box-shadow: 0 0 10px gray;
}
</style>