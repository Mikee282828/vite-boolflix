<script>
import store from "../data/store.js";
export default {
    data() {
        return {
            store
        }
    }
}
</script>

<template>
    <h2>MOVIES</h2>
    <div class="movie" v-for="element in store.searchFilm" v-show="store.searchFilm != []">
        <img :src="`https://image.tmdb.org/t/p/original${element.backdrop_path}`" alt=""> <br>
        titolo: {{ element.title }} <br>
        titolo originale: {{ element.original_title }} <br>
        lingua originale: {{ element.original_language }} <br>
        voto: {{ element.vote_average }}
    </div>
</template>

<style scoped>
.movie {
    margin-bottom: 3rem;
}
img{
    width:10rem;
}
</style>