<template>
  <div id="app">
    <AppHeader />
    <input type="text" v-model="name" />
    <button @click="searchName">Search</button>
    <h2>FILM</h2>
    <div class="card" v-for="(movie, index) in movies" :key="index">
      <div>Titolo: {{ movie.title }}</div>
      <div>Titolo originale: {{ movie.original_title }}</div>
      <div>
        Lingua originale:
        <img :src="getFlag(movie.original_language)" alt="" />
      </div>
      <div>Voto: {{ movie.vote_average }}</div>
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
      name: "",
    };
  },
  methods: {
    searchName() {
      axios
        .get(
          `https://api.themoviedb.org/3/search/movie?api_key=666c60c46937c74d09eb7327646c579d&language=it-IT&query=${this.name}`
        )
        .then((results) => {
          this.movies = results.data.results;
          console.log(this.movies);
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
</style>