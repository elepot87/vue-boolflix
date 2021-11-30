<template>
  <main class="main-container">
    <ul class="container-film">
      <li v-if="films.length > 0 || series.length > 0">
        <Card
          class="film-item"
          v-for="(film, index) in films"
          :key="`film-${index}`"
          :title="film.title"
          :subtitle="film.original_title"
          :info1="film.original_language"
          :info2="film.vote_average"
        />
        <Card
          class="series-item"
          v-for="(serie, index) in series"
          :key="`series-${index}`"
          :title="serie.name"
          :subtitle="serie.original_name"
          :info1="serie.original_language"
          :info2="serie.vote_average"
        />
      </li>
      <div class="no-result" v-else>La ricerca non ha prodotto risultati</div>
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
    series: Array,
  },
};
</script>

<style scoped lang="scss">
@import "@/styles/main";
</style>
