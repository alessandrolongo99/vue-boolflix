<template>
  <div
    @mouseover="hover = true"
    @mouseleave="hover = false"
    class="col-3 g-3 position-relative"
  >
    <div class="poster">
      <img :src="buildPosterPath(poster)" :alt="title" />
    </div>

    <div v-show="hover" class="al-info text-white position-absolute">
      <div>Titolo: {{ title }}</div>
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
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data: function () {
    return {
      posterInitialPath: "https://image.tmdb.org/t/p/",
      hover: false,
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

.al-info {
  background-color: rgba(0, 0, 0, 0.582);
  background-image: url();
  height: 100%;
  width: 100%;
  top: 0;
  left: 0;
  margin: 0 8px;
}
</style>