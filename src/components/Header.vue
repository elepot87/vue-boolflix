<template>
  <header class="header">
    <form action="">
      <input
        type="text"
        class="form-control"
        placeholder=">Search film"
        v-model.trim="searchText"
        @keyup="$emit('performeSearch', searchText)"
      />
      <button
        type="submit"
        @click.prevent="$emit('performeSearch', searchText)"
      >
        Search
      </button>
    </form>
  </header>
</template>

<script>
export default {
  name: "Header",
  data() {
    return {
      searchText: "",
    };
  },
};
</script>

<style scoped lang="scss">
@import "@/styles/header";
</style>
