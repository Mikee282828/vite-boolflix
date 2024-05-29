<script>
import axios from 'axios';
import store from "../data/store.js";
export default {
    data() {
        return {
            store
        }
    },
    methods: {
        search() {
            const tv = {
                method: 'GET',
                url: 'https://api.themoviedb.org/3/search/tv',
                params: {
                    query: this.store.searchText,
                    include_adult: 'true',
                    language: 'it-IT',
                    page: '1',
                    api_key: '1a03cede7fddf759ac17995c787cc6e0',
                },
            };
            const movie = {
                method: 'GET',
                url: 'https://api.themoviedb.org/3/search/movie',
                params: {
                    query: this.store.searchText,
                    include_adult: 'true',
                    language: 'it-IT',
                    page: '1',
                    api_key: '1a03cede7fddf759ac17995c787cc6e0',
                },
            };

            axios
                .request(movie)
                .then((response) => {
                    this.store.searchFilm = response.data.results;
                })
                .catch(function (error) {
                    console.error(error);
                });
            axios
                .request(tv)
                .then((response) => {
                    this.store.searchTv = response.data.results;
                })
                .catch(function (error) {
                    console.error(error);
                });
        }
    }
}
</script>

<template>

    <header>
        <div class="logo">
            <h1>BOOLFLIX</h1>
        </div>
        <div class="searchbar">
            <input type="text" v-model="store.searchText" :input="search()" placeholder="Cerca">
        </div>
    </header>

</template>

<style scoped>
.logo{
    color:red;
}
header{
    position:fixed;
    display:flex;
    width:100%;
    padding:3rem;
    background-color: black;
    justify-content: space-between;
}
.searchbar{
    font-size: 2rem;
}
</style>