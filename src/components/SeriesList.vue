<template>
  <div class="row">
    <div class="col d-flex flex-wrap justify-content-center gap-3">
      <div class="card" v-for="serie in series" :key="serie.id">
        <span><b>Titolo:</b> {{ serie.name }}</span>
        <span><b>Titolo originale:</b> {{ serie.original_name }}</span>
        <span><b>Lingua originale:</b> {{ serie.original_language }}</span>
        <span><b>Voto:</b> {{ serie.vote_average }}</span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "SeriesList",
  props: {
    series: Array,
  },
};
</script>

<style scoped lang="scss">
.card {
  width: 250px;
}
</style>