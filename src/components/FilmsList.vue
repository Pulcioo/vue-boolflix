<template>
  <div class="row">
    <div class="col d-flex flex-wrap justify-content-center gap-3">
      <div class="card" v-for="film in films" :key="film.id">
        <span><b>Titolo:</b> {{ film.title }}</span>
        <span><b>Titolo originale:</b> {{ film.original_title }}</span>
        <span><b>Lingua originale:</b> {{ film.original_language }}</span>
        <span><b>Voto:</b> {{ film.vote_average }}</span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "FilmsList",
  props: {
    films: Array,
  },
};
</script>

<style scoped lang="scss">
.card {
  width: 250px;
}
</style>