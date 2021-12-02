<template>
  <header class="header d-flex">
    <div class="header-left d-flex">
      <a href="#" class="brand-link">
        <img
          :src="require(`@/assets/img/logo_verdepastello.png`)"
          alt="logo
      Verdepastello"
          class="logo-header"
        />
      </a>
      <div class="name-app">PastelloFlix Streaming</div>
    </div>
    <!-- Header center -->
    <nav class="header-center">
      <ul class="main-menu d-flex">
        <li class="menu-item"><a href="#" class="link-menu">Serie Tv</a></li>
        <li class="menu-item"><a href="#" class="link-menu">Film</a></li>
        <li class="menu-item">
          <a href="#" class="link-menu">Nuovi e popolari</a>
        </li>
        <li class="menu-item">
          <a href="#" class="link-menu">La mia lista</a>
        </li>
        <li class="menu-item">
          <a href="#" class="link-menu">Guarda di nuovo</a>
        </li>
      </ul>
    </nav>
    <!-- Header right -->
    <div class="header-right d-flex">
      <div class="info-user d-flex">
        <div class="dropdown" @click="menuActive()">
          <i class="fas fa-bell icon-header"></i>
          <ul class="menu-dropdown" :class="{ active: isActive }">
            <li class="item-dropdown">È uscito Dominion</li>
            <li><span class="divider"></span></li>
            <li class="item-dropdown">Le novità!</li>
          </ul>
        </div>
        <div class="dropdown user" @click="menuActive()">
          <i class="fas fa-user icon-header"></i>
          <ul class="menu-dropdown" :class="{ active: isActive }">
            <li class="item-dropdown">Account</li>
            <li><span class="divider"></span></li>
            <li class="item-dropdown">Pagamenti</li>
            <li><span class="divider"></span></li>
            <li class="item-dropdown">Ordini</li>
            <li><span class="divider"></span></li>
            <li class="item-dropdown">I tuoi preferiti</li>
          </ul>
        </div>
      </div>
      <form action="">
        <input
          type="text"
          id="input-site"
          class="form-control-site"
          placeholder="Search film or tv series"
          v-model.trim="searchText"
          @keyup="$emit('performeSearch', searchText)"
        />
        <button
          class="button-site"
          type="submit"
          @click.prevent="$emit('performeSearch', searchText)"
        >
          Search
        </button>
        <button
          class="button-site"
          type="reset"
          @click.prevent="clearSearchInput"
        >
          Reset
        </button>
      </form>
    </div>
  </header>
</template>

<script>
export default {
  name: "Header",
  data() {
    return {
      searchText: "",
      isActive: false,
    };
  },
  methods: {
    clearSearchInput() {
      // reset dato
      this.searchText = "";
      // emit
      this.$emit("performeSearch", this.searchText);
    },
    menuActive() {
      this.isActive = !this.isActive;
    },
  },
};
</script>

<style scoped lang="scss">
@import "@/styles/header";
</style>
