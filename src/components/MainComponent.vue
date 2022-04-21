<template>
  <div class="container-fluid">
    <div class="row">
      <div class="col">
        <span>FILM</span>
        <FilmsList :films="films" />
      </div>
    </div>
    <div class="row">
      <div class="col">
        <span>SERIE TV</span>
        <SeriesList :series="series" />
      </div>
    </div>
  </div>
</template>

<script>
import FilmsList from "@/components/FilmsList.vue";
import SeriesList from "@/components/SeriesList.vue";

export default {
  name: "MainComponent",
  components: {
    FilmsList,
    SeriesList,
  },
  props: {
    films: Array,
    series: Array,
  },
};
</script>

<style scoped lang="scss">
</style>