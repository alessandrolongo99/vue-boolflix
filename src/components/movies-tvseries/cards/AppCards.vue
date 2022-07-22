<template>
  <div class="card col-3">
    <div>
      <img :src="buildPosterPath(poster)" :alt="title" />
    </div>

    <div>Titolo: {{ title }}</div>
    <div>Titolo originale: {{ originalTitle }}</div>

    <div>
      Lingua originale:
      <img class="flag" :src="getFlag(language)" :alt="language" />
    </div>

    <div>
      Voto:
      <i
        v-for="(star, index) in changeVoteInStars(vote)"
        :key="index"
        class="fa-solid fa-star"
      ></i>
    </div>
  </div>
</template>

<script>
export default {
  data: function () {
    return {
      posterInitialPath: "https://image.tmdb.org/t/p/",
    };
  },

  props: {
    poster: String,
    title: String,
    originalTitle: String,
    language: String,
    vote: Number,
  },

  methods: {
    buildPosterPath(input) {
      return this.posterInitialPath + "w342" + input;
    },

    getFlag(language) {
      return `https://www.unknown.nu/flags/images/${language}-100`;
    },

    changeVoteInStars(vote) {
      return Math.ceil(vote / 2);
    },
  },
};
</script>

<style scoped>
@import "https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.1.1/css/all.min.css";

.card {
  padding: 1rem 0;
}

.flag {
  height: 1rem;
}
</style>