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
        params: {
          query: this.searchText,
          include_adult: 'true',
          language: 'it-IT',
          page: '1',
          api_key: '1a03cede7fddf759ac17995c787cc6e0',
        },
      };

      axios
        .request(options)
        .then((response)=> {
          this.store = response.data.results;
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

<!-- "id": 19603,
"original_language": "en",
"original_title": "Ciao",
"overview": "A man learns that his late friend had a secret online lover who is on the way from Italy.",
"popularity": 6.625,
"poster_path": "/fvgR62s7bJizAS8xnGZCHmZrPbw.jpg",
"release_date": "2008-12-05",
"title": "Ciao",
"video": false,
"vote_average": 5.7,
"vote_count": 38 -->

<template>

  <div class="searchbar">
    <input type="text" v-model="searchText">
    <button @click="searchMovie()">Submit</button>
  </div>

  <div class="movie" v-for="element in store">
    titolo: {{ element.title }} <br>
    titolo originale: {{ element.original_title }} <br>
    lingua originale: {{ element.original_language }} <br>
    voto: {{ element.vote_average }}
  </div>

</template>

<style scoped>
.movie{
  margin-bottom:3rem;
}
</style>
