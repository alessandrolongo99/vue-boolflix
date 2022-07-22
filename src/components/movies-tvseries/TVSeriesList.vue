<template>
  <div class="row">
    <h2 class="text-white pt-5 mb-0">SERIE TV</h2>
    <AppCards
      v-for="series in seriesFromMain"
      :key="series.id"
      :poster="series.poster_path"
      :title="series.name"
      :originalTitle="series.original_name"
      :language="series.original_language"
      :vote="series.vote_average"
      :overview="series.overview"
    />
  </div>
</template>

<script>
import AppCards from "./cards/AppCards.vue";

export default {
  name: "TVSeriesList",
  components: {
    AppCards,
  },

  props: {
    seriesFromMain: Array,
  },
};
</script>

<style scoped>
</style>