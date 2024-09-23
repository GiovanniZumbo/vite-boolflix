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
        }
    }


}
</script>

<template>

    <nav id="header" class="navbar bg-dark position-sticky top-0 start-0">
        <div class="container-fluid d-flex justify-content-between">
            <a class="navbar-brand text-danger">BOOTFLIX</a>
            <div class="d-flex" id="header-right">
                <input class="form-control me-2" type="text" placeholder="Search..." v-model="userRequest"
                    @keyup.enter="triggerCallDatabase(userRequest)">
                <button class="btn btn-outline-danger" type="button"
                    @click="triggerCallDatabase(userRequest)">Search</button>
            </div>
        </div>
    </nav>


</template>

<style lang="scss" scoped>
#header {
    height: 4rem;
    z-index: 1;

}
</style>