<template>
  <div id="app">
    <Header @performeSearch="searchList" />
    <Main :films="filmList" :series="seriesList" v-if="noEmptyInput" />
    <Error v-else />
  </div>
</template>

<script>
import axios from "axios";
import Header from "@/components/Header.vue";
import Main from "@/components/Main.vue";
import Error from "@/components/Error.vue";

export default {
  name: "App",
  components: {
    Header,
    Main,
    Error,
  },
  data() {
    return {
      filmList: [],
      seriesList: [],
      searchTextInput: "",
    };
  },
  // created() {
  //   this.getSeriesList();
  // },

  methods: {
    searchList(text) {
      this.searchTextInput = text;
      this.getFilmList(this.searchTextInput);
      this.getSeriesList(this.searchTextInput);
    },
    getFilmList(query) {
      if (query === "") {
        this.filmList = [];
      } else {
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
          })
          .catch((err) => console.log(err));
      }
    },
    getSeriesList(query) {
      if (query === "") {
        this.seriesList = [];
      } else {
        axios
          .get("https://api.themoviedb.org/3/search/tv", {
            params: {
              api_key: "694d4228c101f485c77573eb27c4523a",
              query: query,
              language: "it-IT",
            },
          })
          .then((response) => {
            console.log(response.data.results);
            this.seriesList = response.data.results;
          })
          .catch((err) => console.log(err));
      }
    },
  },
  computed: {
    noEmptyInput() {
      return this.searchTextInput !== "";
    },
  },
};
</script>

<style lang="scss">
@import "@/styles/global";
</style>
