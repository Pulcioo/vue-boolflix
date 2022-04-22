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
          <ul class="list">
            <li><b>Titolo:</b> {{ serie.title }}</li>
            <li><b>Titolo originale:</b> {{ serie.original_title }}</li>
            <li>
              <b>Lingua originale: </b
              ><img
                v-if="avilableFlags.includes(serie.original_language)"
                :src="`./flags/${serie.original_language}.png`"
                :alt="serie.original_language"
                class="flag"
              />
              <span v-else>{{ serie.original_language }}</span>
            </li>
            <li>
              <b>Voto:</b
              ><span
                v-for="(star, index) in intNumber(serie.vote_average)"
                :key="index"
                ><i class="fa-solid fa-star"></i
              ></span>
            </li>
          </ul>
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
  data() {
    return {
      avilableFlags: ["it", "fr", "es", "en", "de"],
    };
  },
  methods: {
    intNumber(number) {
      return Math.ceil(number / 2);
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

  .list {
    list-style-type: none;
    padding-inline-start: 3px;
    margin-top: 3px;

    .flag {
      width: 20px;
    }
  }
}
</style>