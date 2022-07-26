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
      :cast="searchCast(series.id)"
    />
  </div>
</template>

<script>
import AppCards from "./cards/AppCards.vue";
import axios from "axios";

export default {
  name: "TVSeriesList",
  components: {
    AppCards,
  },

  data: function(){
    return{
      cast: [],
    }
  },

  props: {
    seriesFromMain: Array,
  },

  methods: {
    searchCast(id) {
      axios
        .get(
          `https://api.themoviedb.org/3/tv/${id}/credits?api_key=666c60c46937c74d09eb7327646c579d`
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