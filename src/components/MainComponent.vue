<template>
  <div class="container-fluid">
    <div class="row">
      <div class="col p-5">
        <span v-show="films.length > 0">FILM</span>
        <FilmsList :films="films" :imageUrl="imageUrl" />
      </div>
    </div>
    <div class="row">
      <div class="col p-5">
        <span v-show="series.length > 0">SERIE TV</span>
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
      imageUrl: "https://image.tmdb.org/t/p/w342/",
    };
  },
};
</script>

<style scoped lang="scss">
span {
  font-size: 25px;
  color: white;
}
</style>