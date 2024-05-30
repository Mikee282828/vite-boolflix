<script>
import store from "./data/store.js";
import Movies from "./components/Movies.vue";
import Tv from "./components/Tv.vue";
import AppHeader from "./components/AppHeader.vue";
export default {
  components: {
    Movies,
    Tv,
    AppHeader
  },
  data() {
    return {
      store,
    }
  }
}
</script>

<template>
  <AppHeader />
  <div class="container" v-show="store.searchText != ''">
    <h1 class="moviesHeader">MOVIES</h1>
    <div class="my_display_flex">
      <Movies v-for="element in store.searchFilm" :poster="element.poster_path" :title="element.title"
        :originalTitle="element.original_title" :vote="element.vote_average" :overview="element.overview" />
    </div>
  </div>

  <div class="container" v-show="store.searchText != ''">
    <h1 class="tvsHeader">Tv Series</h1>
    <div class="my_display_flex">
      <Tv v-for="element in store.searchTv" :poster="element.poster_path" :name="element.name"
        :originalName="element.original_name" :vote="element.vote_average" :overview="element.overview" />
    </div>
  </div>

</template>

<style scoped>
.my_display_flex {
  display: flex;
  flex-flow: wrap row;
  gap: calc(5% / 4);
}
.container{
  width:1337px;
  margin:0 auto;
}

.moviesHeader {
  margin-bottom: 3rem;
  padding-top: 12rem;
}

.tvsHeader {
  margin-bottom: 3rem;
}
</style>
