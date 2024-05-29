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
    <div class="container" v-show="store.searchText != ''">
        <h1>TV SERIES</h1>

        <div class="my_display_flex">

            <div class="tv" v-for="element in store.searchTv" v-show="store.searchTv != []">
                <img :src="`https://image.tmdb.org/t/p/original${element.backdrop_path}`" alt=""> <br>
                {{ element.name }} <br>
                {{ element.original_name }} <br>
                {{ element.original_language.toUpperCase() }} <br>
                <i class="fa-solid fa-star" v-for="element in Math.ceil(element.vote_average / 2)"></i><i
                    class="fa-regular fa-star" v-for="element in (5 - Math.ceil(element.vote_average / 2))"></i>
                <!-- voto: {{ Math.ceil(element.vote_average) }} -->
            </div>

        </div>
    </div>

</template>

<style scoped>
h1 {
    margin: 3rem 0;
}

.tv {
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