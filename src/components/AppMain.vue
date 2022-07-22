<template>
  <div>
    <MoviesList :moviesFromMain="moviesFromApp"/>
    <TVSeriesList :seriesFromMain="seriesFromApp"/>
  </div>
</template>

<script>
import MoviesList from "./movies-tvseries/MoviesList.vue";
import TVSeriesList from "./movies-tvseries/TVSeriesList.vue";

export default {
  name: "AppMain",
  components: {
    MoviesList,
    TVSeriesList,
  },

  props:{
    moviesFromApp: Array,
    seriesFromApp: Array,
  },
};
</script>

<style scoped>
</style>