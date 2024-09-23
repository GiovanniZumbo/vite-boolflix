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
    }
}
</script>

<template>
    <h4>MAIN MOVIE CARD</h4>
    CARDLIST
    <div class="card">
        <p class="title">Titolo: "{{ movie.title }}" </p>
        <p class="og-title">Titolo originale: "{{ movie.original_title }}</p>
        <p class="lang">Lingua: {{ movie.original_language }}</p>
        <p class="vote">Voto: {{ movie.vote_average }}</p>
    </div>
</template>

<style scoped></style>