<template>
  <main class="main-container">
    <ul class="container-film">
      <li
        class="film-item"
        v-for="(film, index) in films"
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
import Card from "@/components/Card.vue";
export default {
  name: "Main",
  components: {
    Card,
  },
  props: {
    films: Array,
  },
};
</script>

<style scoped lang="scss">
@import "@/styles/main";
</style>
