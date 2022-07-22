<template>
  <header class="bg-black">
    <div class="container d-flex align-items-center justify-content-between">
      <h1 class="text-danger">BOOLFLIX</h1>
      <input
        type="text"
        placeholder="Search"
        v-model.trim="name"
        @keyup.enter="$emit('search', name)"
      />
    </div>
  </header>
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