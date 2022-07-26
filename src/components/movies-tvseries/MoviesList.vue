<template>
  <div class="row">
    <h2 class="text-white pt-5 mb-0">FILM</h2>
    <AppCards
      v-for="movie in moviesFromMain"
      :key="movie.id"
      :poster="movie.poster_path"
      :title="movie.title"
      :originalTitle="movie.original_title"
      :language="movie.original_language"
      :vote="movie.vote_average"
      :overview="movie.overview"
      :cast="searchCast(movie.id)"
    />
  </div>
</template>

<script>
import AppCards from "./cards/AppCards.vue";
import axios from "axios";

export default {
  name: "MoviesList",
  components: {
    AppCards,
  },

  data: function(){
    return{
      cast: [],
    }
  },

  props: {
    moviesFromMain: Array,
  },

  methods: {
    searchCast(id) {
      axios
        .get(
          `https://api.themoviedb.org/3/movie/${id}/credits?api_key=666c60c46937c74d09eb7327646c579d`
        )
        .then((results) => {
          this.cast = results.data.cast;
        });
        return this.cast;
    },
  },
};
</script>

<style scoped>
</style>