<template>
  <div id="app">
    <Header @performeSearch="searchFilm" />
    <Main :films="filmList" />
  </div>
</template>

<script>
import axios from "axios";
import Header from "@/components/Header.vue";
import Main from "@/components/Main.vue";

export default {
  name: "App",
  components: {
    Header,
    Main,
  },
  data() {
    return {
      filmList: null,
      searchTextInput: "",
    };
  },
  created() {
    // this.getFilmList();
  },
  methods: {
    searchFilm(text) {
      console.log(text);
      this.searchTextInput = text;
      this.getFilmList(this.searchTextInput);
    },
    getFilmList(query) {
      axios
        .get("https://api.themoviedb.org/3/search/movie", {
          params: {
            api_key: "694d4228c101f485c77573eb27c4523a",
            query: query,
            language: "it-IT",
          },
        })
        .then((response) => {
          console.log(response.data.results);
          this.filmList = response.data.results;
          // console.log(this.filmList);
        })
        .catch((err) => console.log(err));
    },
  },
};
</script>

<style lang="scss">
@import "@/styles/global";
</style>
