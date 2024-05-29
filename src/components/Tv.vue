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
    <h2>TV SERIES</h2>
    <div class="tv" v-for="element in store.searchTv" v-show="store.searchTv != []">
        <img :src="`https://image.tmdb.org/t/p/original${element.backdrop_path}`" alt=""> <br>
        titolo: {{ element.name }} <br>
        titolo originale: {{ element.original_name }} <br>
        lingua originale: {{ element.original_language }} <br>
        voto: {{ element.vote_average }}
    </div>
</template>

<style scoped>
.tv {
    margin-bottom: 3rem;
}
img{
    width:10rem;
}
</style>