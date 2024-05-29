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
    <h1>TV SERIES</h1>

    <div class="my_display_flex">

        <div class="tv" v-for="element in store.searchTv" v-show="store.searchTv != []">
            <img :src="`https://image.tmdb.org/t/p/original${element.backdrop_path}`" alt=""> <br>
            titolo: {{ element.name }} <br>
            titolo originale: {{ element.original_name }} <br>
            lingua originale: {{ element.original_language }} <br>
            voto: {{ Math.ceil(element.vote_average) }}
        </div>
        
    </div>
</template>

<style scoped>
h1{
    margin:3rem 0;
}
.tv {
    margin-bottom: 3rem;
    width:19%;
}
img{
    width:10rem;
}
.my_display_flex{
    display: flex;
    flex-flow: wrap row;
    gap:calc(5% / 4);
}
</style>