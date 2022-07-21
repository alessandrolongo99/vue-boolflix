<template>
  <div id="app">
    <AppHeader />
    <input type="text" v-model="name" />
    <button @click="searchMedia">Search</button>

    <h2>FILM</h2>
    <div class="card" v-for="(movie, movieIndex) in movies" :key="movieIndex">
      <div>
        <img :src="buildPosterPath(movie.poster_path)" alt="" />
      </div>
      <div>Titolo: {{ movie.title }}</div>
      <div>Titolo originale: {{ movie.original_title }}</div>
      <div>
        Lingua originale:
        <img class="flag" :src="getFlag(movie.original_language)" alt="" />
      </div>
      <div>
        <i class="fa-solid fa-star"></i>
      </div>
    </div>

    <h2>SERIE TV</h2>
    <div
      class="card"
      v-for="(series, seriesIndex) in TVSeries"
      :key="'a' + seriesIndex"
    >
      <div>
        <img :src="buildPosterPath(series.poster_path)" alt="" />
      </div>
      <div>Titolo: {{ series.name }}</div>
      <div>Titolo originale: {{ series.original_name }}</div>
      <div>
        Lingua originale:
        <img class="flag" :src="getFlag(series.original_language)" alt="" />
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
      stars: 0,
      posterInitialPath: "https://image.tmdb.org/t/p/",
      apiKey: "666c60c46937c74d09eb7327646c579d",
    };
  },
  methods: {
    searchMedia() {
      this.searchMovies();
      this.searchTVSeries();
    },
    buildPosterPath(input) {
      return this.posterInitialPath + "w154" + input;
    },
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
    changeVoteInStars(vote){
      this.stars = Math.ceil(vote / 2)
    }
  },
};
</script>

<style lang="scss">
@import 'https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.1.1/css/all.min.css';

.card {
  padding: 1rem 0;
}

.flag {
  height: 1rem;
}
</style>