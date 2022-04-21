<template>
  <div class="row m-3">
    <div class="col d-flex flex-wrap justify-content-center gap-4">
      <div class="card" v-for="serie in series" :key="serie.id">
        <div v-if="serie.poster_path !== null">
          <img :src="imageUrl + serie.poster_path" :alt="serie.name" />
        </div>
        <div v-else>
          <img
            class="w-100"
            src="@/assets/image-not-found.png"
            alt="not-found"
          />
        </div>
        <div class="card_text d-flex flex-column">
          <span><b>Titolo:</b> {{ serie.name }}</span>
          <span><b>Titolo originale:</b> {{ serie.original_name }}</span>
          <span><b>Lingua originale:</b> {{ serie.original_language }}</span>
          <span><b>Voto:</b> {{ intNumber(serie.vote_average) }}</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "SeriesList",
  props: {
    series: Array,
    imageUrl: String,
  },
  methods: {
    intNumber(number) {
      return Math.ceil(number);
    },
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