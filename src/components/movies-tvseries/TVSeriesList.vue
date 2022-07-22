<template>
  <div>
    <h2>SERIE TV</h2>
    <!-- <AppCards /> -->
  </div>
</template>

<script>
// import AppCards from "./cards/AppCards.vue";

export default {
  name: "TVSeriesList",
  components: {
    // AppCards,
  },

  props: {
    seriesFromMain: Array,
  },
};
</script>

<style scoped>
</style>