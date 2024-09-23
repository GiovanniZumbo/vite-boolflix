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
        triggerCallDatabase(request) {
            this.$emit('callDatabase', request);
            this.userRequest = "";
        }
    }


}
</script>

<template>

    <nav id="header" class="navbar position-sticky top-0 start-0">
        <div class="container-fluid d-flex justify-content-between">
            <img src="/src/assets/logo_boolflix.png" alt="">
            <div class="d-flex" id="header-right">
                <input class="form-control me-2" type="text" placeholder="Search..." v-model="userRequest"
                    @keyup.enter="triggerCallDatabase(userRequest)">
                <button class="btn btn-outline-danger bg-danger text-light" type="button"
                    @click="triggerCallDatabase(userRequest)">Search</button>
            </div>
        </div>
    </nav>


</template>

<style lang="scss" scoped>
#header {
    height: 5rem;
    z-index: 1;
    background-color: black;
    padding: 1rem 0;
    margin-bottom: 2rem;

    img {
        width: 9rem;
    }

}
</style>