<script>
//Store
import { store } from '../store'


export default {
    data() {
        return {
            userRequest: "",
            store
        }
    },

    methods: {
        triggerCallForMovies(request) {
            this.$emit('callForMovies', request);
        }
    }


}
</script>

<template>
    <h1>HEADER</h1>
    <div class="input-group mb-3 w-25">
        <input type="text" class="form-control" placeholder="Search..." v-model="userRequest"
            @keyup.enter="triggerCallForMovies(userRequest)">
        <button class="btn btn-outline-secondary" type="button" id="button-addon2"
            @click="triggerCallForMovies(userRequest)">Search
        </button>
    </div>


</template>

<style scoped></style>