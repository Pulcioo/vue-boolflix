<template>
  <div class="container-fluid">
    <FilmsList :films="films" />
  </div>
</template>

<script>
import FilmsList from "@/components/FilmsList.vue";

export default {
  name: "MainComponent",
  components: {
    FilmsList,
  },
  props: {
    films: Array,
  },
};
</script>

<style scoped lang="scss">
</style>