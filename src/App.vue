<template>
  <div id="app">
    <AppHeader />
    <input type="text" v-model="name" />
    <button @click="searchMovies">Search</button>
    <button @click="searchTVSeries">Search</button>
    <h2>FILM</h2>
    <div class="card" v-for="(movie, movieIndex) in movies" :key="movieIndex">
      <div>Titolo: {{ movie.title }}</div>
      <div>Titolo originale: {{ movie.original_title }}</div>
      <div>
        Lingua originale:
        <img :src="getFlag(movie.original_language)" alt="" />
      </div>
      <div>Voto: {{ movie.vote_average }}</div>
    </div>
    <h2>SERIE TV</h2>
    <div class="card" v-for="(series, seriesIndex) in TVSeries" :key="seriesIndex">
      <div>Titolo: {{ series.name }}</div>
      <div>Titolo originale: {{ series.original_name }}</div>
      <div>
        Lingua originale:
        <img :src="getFlag(series.original_language)" alt="" />
      </div>
      <div>Voto: {{ series.vote_average }}</div>
    </div>
  </div>
</template>

<script>
import AppHeader from "./components/AppHeader.vue";
import axios from "axios";

export default {
  name: "App",
  components: {
    AppHeader,
  },
  data: function () {
    return {
      movies: [],
      TVSeries: [],
      name: "",
      apiKey: "666c60c46937c74d09eb7327646c579d",
    };
  },
  methods: {
    searchMovies() {
      axios
        .get(
          `https://api.themoviedb.org/3/search/movie?api_key=${this.apiKey}&language=it-IT&query=${this.name}`
        )
        .then((results) => {
          this.movies = results.data.results;
          console.log(this.movies);
        });
    },
    searchTVSeries() {
      axios
        .get(
          `https://api.themoviedb.org/3/search/tv?api_key=${this.apiKey}&language=it-IT&query=${this.name}`
        )
        .then((results) => {
          this.TVSeries = results.data.results;
          console.log(this.TVSeries);
        });
    },
    getFlag(language) {
      return `https://www.unknown.nu/flags/images/${language}-100`;
    },
  },
};
</script>

<style lang="scss">
.card {
  padding: 1rem 0;
}
img{
  height: 1rem;
}
</style>