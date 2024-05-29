<script>
import store from "./data/store.js";
import axios from 'axios';
export default {
  data() {
    return {
      store,
      searchText: ""
    }
  },
  methods: {
    searchMovie() {
      const options = {
        method: 'GET',
        url: 'https://api.themoviedb.org/3/search/movie',
        params: { query: this.searchText, include_adult: 'true', language: 'it-IT', page: '1' },
        headers: {
          accept: 'application/json',
          Authorization: 'Bearer 1a03cede7fddf759ac17995c787cc6e0'
        }
      };

      axios
        .request(options)
        .then(function (response) {
          console.log(response.data);
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
    <input type="text" v-model="searchText">
    <button @click="searchMovie()">Submit</button>
  </div>
  <pre></pre>
</template>

<style scoped></style>
