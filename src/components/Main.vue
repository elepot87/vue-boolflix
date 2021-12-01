<template>
  <main class="main-container">
    <ul class="container-list" v-if="films.length > 0 || series.length > 0">
      <li v-for="(film, index) in films" :key="`film-${index}`">
        <Card
          class="film-item"
          :poster="film.poster_path"
          :title="film.title"
          :subtitle="film.original_title"
          :info1="film.original_language"
          :info2="film.vote_average"
          :text="film.overview"
        />
      </li>
      <li v-for="(serie, index) in series" :key="`series-${index}`"></li>
    </ul>
    <div class="no-result" v-else>La ricerca non ha prodotto risultati</div>
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
    series: Array,
  },
};
</script>

<style scoped lang="scss">
@import "@/styles/main";
</style>
