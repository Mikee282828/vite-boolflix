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
    <h1>MOVIES</h1>
    <div class="my_display_flex">

        <div class="movie" v-for="element in store.searchFilm" v-show="store.searchFilm != []">
            <img :src="`https://image.tmdb.org/t/p/original${element.backdrop_path}`" alt=""> <br>
            {{ element.title }} <br>
            {{ element.original_title }} <br>
            {{ element.original_language().toUpperCase() }} <br>
            <i class="fa-solid fa-star" v-for="element in Math.ceil(element.vote_average / 2)"></i><i
                class="fa-regular fa-star" v-for="element in (5 - Math.ceil(element.vote_average / 2))"></i>
            <!-- voto: {{ Math.ceil(element.vote_average / 2) }} -->
        </div>

    </div>
</template>

<style scoped>
h1 {
    margin: 3rem 0;
}

.movie {
    margin-bottom: 3rem;
    width: 19%;
    background-color: aliceblue;
    color: black;
}

img {
    width: 100%;
}

.my_display_flex {
    display: flex;
    flex-flow: wrap row;
    gap: calc(5% / 4);
}
</style>