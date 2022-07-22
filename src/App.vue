<template>
  <div id="app">
    <AppHeader @search="searchMedia" />
    <AppMain :moviesFromApp="movies" :seriesFromApp="TVSeries" />
  </div>
</template>

<script>
import AppHeader from "./components/AppHeader.vue";
import AppMain from "./components/AppMain.vue";
import axios from "axios";

export default {
  name: "App",
  components: {
    AppHeader,
    AppMain,
  },

  data: function () {
    return {
      apiInitalPath: "https://api.themoviedb.org/3/search/",
      apiKey: "666c60c46937c74d09eb7327646c579d",
      movies: [],
      TVSeries: [],
    };
  },

  methods: {
    searchMedia(name) {
      axios
        .get(
          `${this.apiInitalPath}movie?api_key=${this.apiKey}&language=it-IT&query=${name}`
        )
        .then((results) => {
          this.movies = results.data.results;
        });

      axios
        .get(
          `${this.apiInitalPath}tv?api_key=${this.apiKey}&language=it-IT&query=${name}`
        )
        .then((results) => {
          this.TVSeries = results.data.results;
        });
    },
  },

  created() {
    axios
      .get(
        `https://api.themoviedb.org/3/trending/movie/day?api_key=${this.apiKey}`
      )
      .then((results) => {
        this.movies = results.data.results;
      });

    axios
      .get(
        `https://api.themoviedb.org/3/trending/tv/day?api_key=${this.apiKey}`
      )
      .then((results) => {
        this.TVSeries = results.data.results;
      });
  },
};
</script>

<style lang="scss">
@import "~bootstrap/scss/bootstrap";
</style>