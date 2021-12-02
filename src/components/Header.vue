<template>
  <header class="header">
    <div class="header-left">
      <a href="#" class="brand-link">
        <img
          :src="require(`@/assets/img/logo_verdepastello.png`)"
          alt="logo
      Verdepastello"
          class="logo-header"
        />
      </a>
      <a href="https://fontmeme.com/netflix-font/" target="_blank"
        ><img
          src="https://fontmeme.com/permalink/211202/07bdeb0a689bad366cebdb92ed30424b.png"
          alt="netflix-font"
          border="0"
          class="logo-pastelloflix"
      /></a>
      <!-- <div class="name-app">PastelloFlix Streaming</div> -->
    </div>
    <!-- Header center -->
    <nav class="header-center">
      <i class="fas fa-bars menu-toggle-mobile"></i>
      <ul class="main-menu">
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
    <div class="header-right">
      <!-- <div class="info-user d-flex">
        <div class="dropdown-custom" @click="menuActive()">
          <i class="fas fa-bell icon-header"></i>
          <ul class="menu-dropdown-custom" :class="{ active: isActive }">
            <li class="item-dropdown">È uscito Dominion</li>
            <li><span class="divider"></span></li>
            <li class="item-dropdown">Le novità!</li>
          </ul>
        </div>
      
        <div class="dropdown-custom user" @click="menuActive()">
          <i class="fas fa-user icon-header"></i>
          <ul class="menu-dropdown-custom">
            <li class="item-dropdown">Account</li>
            <li><span class="divider"></span></li>
            <li class="item-dropdown">Pagamenti</li>
            <li><span class="divider"></span></li>
            <li class="item-dropdown">Guarda ancora</li>
            <li><span class="divider"></span></li>
            <li class="item-dropdown">I tuoi preferiti</li>
          </ul>
        </div>
      </div> -->
      <!-- Bootstrap Dropdown-->
      <div class="dropdown">
        <button
          class="btn dropdown-toggle"
          type="button"
          id="dropdownMenuButton"
          data-toggle="dropdown"
          aria-haspopup="true"
          aria-expanded="false"
        >
          <i class="fas fa-bell icon-header"></i>
        </button>
        <div class="dropdown-menu" aria-labelledby="dropdownMenuButton">
          <a class="dropdown-item" href="#">È uscito Dominion</a>
          <a class="dropdown-item" href="#">Le novità!</a>
          <a class="dropdown-item" href="#">Trailer</a>
        </div>
      </div>
      <div class="dropdown">
        <button
          class="btn dropdown-toggle"
          type="button"
          id="dropdownMenuButton"
          data-toggle="dropdown"
          aria-haspopup="true"
          aria-expanded="false"
        >
          <i class="fas fa-user icon-header"></i>
        </button>
        <div
          class="dropdown-menu"
          aria-labelledby="dropdownMenuButton"
          id="custom-menu"
        >
          <a class="dropdown-item" href="#">Account</a>
          <a class="dropdown-item" href="#">Pagamenti</a>
          <a class="dropdown-item" href="#">Guarda ancora</a>
          <a class="dropdown-item" href="#">I tuoi preferiti</a>
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
    // menuActive() {
    //   this.isActive = !this.isActive;
    // },
  },
};
</script>

<style scoped lang="scss">
@import "@/styles/header";
</style>
