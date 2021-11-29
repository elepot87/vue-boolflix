<template>
  <div class="container-card">
    <h4 class="title">{{ title }}</h4>
    <h5 class="title-original">{{ subtitle }}</h5>
    <div class="language">{{ info1 }}</div>
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
};
</script>

<style scoped lang="scss">
@import "@/styles/card";
</style>
