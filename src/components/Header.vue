<template>
  <header class="header d-flex">
    <a href="#">
      <img
        src="require(@/assets/img/logo-verdepastello.png)"
        alt="logo Verdepastello"
      />
    </a>
    <form action="">
      <input
        type="text"
        class="form-control"
        placeholder=">Search film or tv series"
        v-model.trim="searchText"
        @keyup="$emit('performeSearch', searchText)"
      />
      <button
        type="submit"
        @click.prevent="$emit('performeSearch', searchText)"
      >
        Search
      </button>
      <button type="reset" @click.prevent="clearSearchInput">Reset</button>
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
  methods: {
    clearSearchInput() {
      // reset dato
      this.searchText = "";
      // emit
      this.$emit("performeSearch", this.searchText);
    },
  },
};
</script>

<style scoped lang="scss">
@import "@/styles/header";
</style>
