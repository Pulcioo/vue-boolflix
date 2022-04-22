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
          <ul class="list">
            <li><b>Titolo:</b> {{ film.title }}</li>
            <li><b>Titolo originale:</b> {{ film.original_title }}</li>
            <li>
              <b>Lingua originale: </b
              ><img
                v-if="avilableFlags.includes(film.original_language)"
                :src="`./flags/${film.original_language}.png`"
                :alt="film.original_language"
                class="flag"
              />
              <span v-else>{{ film.original_language }}</span>
            </li>
            <li>
              <b>Voto:</b
              ><span
                v-for="(star, index) in intNumber(film.vote_average)"
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
  name: "FilmsList",
  props: {
    films: Array,
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