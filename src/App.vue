<script>
import store from "./data/store.js";
import axios from 'axios';
import Movies from "./components/Movies.vue";
import Tv from "./components/Tv.vue";
export default {
  components: {
    Movies,
    Tv
  },
  data() {
    return {
      store,
      searchText: ""
    }
  },
  methods: {
    search() {
      const tv = {
        method: 'GET',
        url: 'https://api.themoviedb.org/3/search/tv',
        params: {
          query: this.searchText,
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
          query: this.searchText,
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
          console.log(response.data.results);
        })
        .catch(function (error) {
          console.error(error);
        });
      axios
        .request(tv)
        .then((response) => {
          this.store.searchTv = response.data.results;
          console.log(response.data.results);
        })
        .catch(function (error) {
          console.error(error);
        });
    }
  },
  created() {

  }
}
</script>

<template>

  <div class="searchbar">
    <input type="text" v-model="searchText" @keyup.enter="search()">
    <button @click="search()">Submit</button>
  </div>

  <Movies />
  <Tv />

</template>

<style scoped></style>
