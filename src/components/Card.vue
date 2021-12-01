<template>
  <div class="container-card">
    <div class="container-poster">
      <img
        v-if="posterOk"
        :src="`https://image.tmdb.org/t/p/w185/${poster}`"
        alt=""
        class="poster"
      />
      <div class="alternative-img" v-else>Immagine non disponibile</div>
    </div>
    <div class="container-info">
      <h4 class="title">{{ title }}</h4>
      <h5 class="title-original">{{ subtitle }}</h5>
      <div class="language">
        <img
          v-if="flag"
          :src="require(`@/assets/img/${info1}.png`)"
          alt="info1"
          class="flag-lang"
        />
        <div class="language" v-else>Lingua: {{ info1 }}</div>
      </div>
      <div class="ratings">
        <i
          class="fas fa-star"
          v-for="n in getVoteStars(info2)"
          :key="`stars-${n}`"
        ></i>
        <i class="far fa-star" v-for="n in 5 - getVoteStars(info2)" :key="n">
        </i>
      </div>
      <div class="overview">{{ text }}</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Card",
  props: {
    poster: String,
    title: String,
    subtitle: String,
    info1: String,
    info2: Number,
    text: String,
  },
  data() {
    return {
      flags: ["en", "it"],
    };
  },
  computed: {
    flag() {
      return this.flags.includes(this.info1);
    },
    posterOk() {
      return this.poster !== undefined && this.poster !== null;
    },
  },
  methods: {
    getVoteStars(number) {
      return Math.ceil(number / 2);
    },
  },
};
</script>

<style scoped lang="scss">
@import "@/styles/card";
</style>
