<template>
  <div class="row m-3">
    <div class="col d-flex flex-wrap justify-content-center gap-4">
      <div class="card" v-for="film in films" :key="film.id">
        <div v-if="film.poster_path !== null">
          <img :src="imageUrl + film.poster_path" :alt="film.name" />
        </div>

        <div v-else>
          <img
            class="w-100"
            src="@/assets/image-not-found.png"
            alt="not-found"
          />
        </div>
        <div class="card_text d-flex flex-column">
          <span><b>Titolo:</b> {{ film.title }}</span>
          <span><b>Titolo originale:</b> {{ film.original_title }}</span>
          <span><b>Lingua originale:</b> {{ film.original_language }}</span>
          <span><b>Voto:</b> {{ film.vote_average }}</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "FilmsList",
  props: {
    films: Array,
    imageUrl: String,
  },
};
</script>

<style scoped lang="scss">
.card {
  width: 185px;

  .card_text {
    font-size: 12px;
  }
}
</style>