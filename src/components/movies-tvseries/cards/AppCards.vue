<template>
  <div class="col-3 g-3">
    <div class="poster">
      <img :src="buildPosterPath(poster)" :alt="title" />
    </div>

    <!-- <div>Titolo: {{ title }}</div>
    <div>Titolo originale: {{ originalTitle }}</div>

    <div>
      Lingua originale:
      <img class="flag" :src="getFlag(language)" :alt="language" />
    </div>

    <div class="stars">
      Voto:
      <i
        v-for="(star, index) in changeVoteInStars(vote)"
        :key="index"
        class="fa-solid fa-star"
      ></i>
    </div> -->
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

<style lang="scss" scoped>
@import "https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.1.1/css/all.min.css";
.flag {
  height: 1rem;
}

.stars i {
  color: gold;
}

.poster {
  height: 100%;
  width: 100%;
  img {
    height: 100%;
    width: 100%;
    object-fit: cover;
    object-position: center top;
  }
}
</style>