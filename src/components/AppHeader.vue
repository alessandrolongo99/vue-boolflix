<template>
  <div>
    <input type="text" v-model="name" @keyup.enter="$emit('search', name)" />
    <button @click="$emit('search', name)">Search</button>
  </div>
</template>

<script>
export default {
  data: function () {
    return {
      name: "",
    };
  },
};
</script>

<style scoped>
</style>