<template>
  <div class="container-fluid">
    <div class="row">
      <div class="col p-5">
        <span>FILM</span>
        <FilmsList :films="films" :imageUrl="imageUrl" />
      </div>
    </div>
    <div class="row">
      <div class="col p-5">
        <span>SERIE TV</span>
        <SeriesList :series="series" :imageUrl="imageUrl" />
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
  data() {
    return {
      imageUrl: "https://image.tmdb.org/t/p/w185/",
    };
  },
};
</script>

<style scoped lang="scss">
.row {
  background-color: #333;
  span {
    font-size: 25px;
    color: white;
  }
}
</style>