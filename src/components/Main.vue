<template>
  <main class="main-container">
    <ul class="container-film">
      <li
        class="film-item"
        v-for="(film, index) in filmList"
        :key="`film-${index}`"
      >
        <Card
          :title="film.title"
          :subtitle="film.original_title"
          :info1="film.original_language"
          :info2="film.vote_average"
        />
        <!-- <h4 class="title">Titolo</h4>
        <h5 class="title-original">Titolo originale</h5>
        <div class="language">Lingua</div>
        <div class="ratings">Voto</div> -->
      </li>
    </ul>
  </main>
</template>

<script>
import axios from "axios";
import Card from "@/components/Card.vue";
export default {
  name: "Main",
  components: {
    Card,
  },
  data() {
    return {
      filmList: [],
    };
  },
  created() {
    this.getFilmList();
  },
  methods: {
    getFilmList() {
      axios
        .get(
          "https://api.themoviedb.org/3/search/movie/?api_key=694d4228c101f485c77573eb27c4523a&query=Fantozzi&language=it-IT"
        )
        .then((response) => {
          console.log(response.data.results);
          this.filmList = response.data.results;
        })
        .catch((err) => console.log(err));
    },
  },
};
</script>

<style scoped lang="scss">
@import "@/styles/main";
</style>
