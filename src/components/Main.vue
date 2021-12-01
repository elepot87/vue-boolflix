<template>
  <main class="main-container">
    <div class="container-list" v-if="films.length > 0 || series.length > 0">
      <!-- Contenitore film -->
      <div class="title-container" v-if="films.length > 0">
        <i class="fas fa-film icon-title"></i>
        <span class="title-text">Film</span>
      </div>
      <div class="container-film">
        <div
          class="list-item"
          v-for="(film, index) in films"
          :key="`film-${index}`"
        >
          <Card
            class="film-item"
            :poster="film.poster_path"
            :title="film.title"
            :subtitle="film.original_title"
            :info1="film.original_language"
            :info2="film.vote_average"
            :text="film.overview"
          />
        </div>
      </div>
      <!-- Contenitore serie tv -->
      <div class="title-container" v-if="series.length > 0">
        <i class="fas fa-tv icon-title"></i>
        <span class="title-text">Serie Tv</span>
      </div>
      <div class="container-series">
        <div
          class="list-item"
          v-for="(serie, index) in series"
          :key="`series-${index}`"
        >
          <Card
            class="film-item"
            :poster="serie.poster_path"
            :title="serie.name"
            :subtitle="serie.original_name"
            :info1="serie.original_language"
            :info2="serie.vote_average"
            :text="serie.overview"
          />
        </div>
      </div>
    </div>
    <!-- No risultati -->
    <div class="no-result d-flex" v-else>
      <div class="text-no-result d-flex">
        Spiacenti, la ricerca non ha prodotto risultati!
      </div>
    </div>
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
