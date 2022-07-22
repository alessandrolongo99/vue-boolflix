<template>
  <div>
    <h2>FILM</h2>
    <AppCards
      v-for="movie in moviesFromMain"
      :key="movie.id"
      :poster="movie.poster_path"
      :title="movie.title"
      :originalTitle="movie.original_title"
      :language="movie.original_language"
      :vote="movie.vote_average"
    />
  </div>
</template>

<script>
import AppCards from "./cards/AppCards.vue";

export default {
  name: "MoviesList",
  components: {
    AppCards,
  },

  props: {
    moviesFromMain: Array,
  },
};
</script>

<style scoped>
</style>