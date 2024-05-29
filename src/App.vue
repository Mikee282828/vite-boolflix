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

<!-- https://image.tmdb.org/t/p/original/Ag6qhzsJd3k1NKuNrG9RmhZDMh7.jpg -->

<template>

  <div class="searchbar">
    <input type="text" v-model="searchText">
    <button @click="search()">Submit</button>
  </div>

  <h2>MOVIES</h2>
  <div class="movie" v-for="element in store.searchFilm" v-show="store.searchFilm != []">
    titolo: {{ element.title }} <br>
    titolo originale: {{ element.original_title }} <br>
    lingua originale: {{ element.original_language }} <br>
    voto: {{ element.vote_average }}
  </div>

  <h2>TV SERIES</h2>
  <div class="movie" v-for="element in store.searchTv" v-show="store.searchTv != []">
    titolo: {{ element.name }} <br>
    titolo originale: {{ element.original_name }} <br>
    lingua originale: {{ element.original_language }} <br>
    voto: {{ element.vote_average }}
  </div>

  <pre>{{ store.searchTv }}</pre>

</template>

<style scoped>
.movie {
  margin-bottom: 3rem;
}
</style>
