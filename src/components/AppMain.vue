<template>
  <div>
    <MoviesList />
  </div>
</template>

<script>
import MoviesList from './movies-tvseries/MoviesList.vue'
import TVSeriesList from './movies-tvseries/TVSeriesList.vue'

export default {
    name: 'AppMain',
    components: {
        MoviesList,
        TVSeriesList,
    }
}
</script>

<style>

</style>