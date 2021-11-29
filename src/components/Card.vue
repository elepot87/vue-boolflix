<template>
  <div class="container-card">
    <h4 class="title">{{ title }}</h4>
    <h5 class="title-original">{{ subtitle }}</h5>
    <div class="language">
      <img
        v-if="flag"
        :src="require(`@/assets/img/${info1}.png`)"
        alt=""
        class="flag-lang"
      />
      <div class="language" v-else>Lingua: {{ info1 }}</div>
    </div>
    <div class="ratings">{{ info2 }}</div>
  </div>
</template>

<script>
export default {
  name: "Card",
  props: {
    title: String,
    subtitle: String,
    info1: String,
    info2: Number,
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
  },
};
</script>

<style scoped lang="scss">
@import "@/styles/card";
</style>
