<template>
  <div class="row m-3">
    <div class="col d-flex flex-wrap justify-content-center gap-4">
      <div class="card" v-for="film in films" :key="film.id">
        <!-- immagine di copertina -->
        <div v-if="film.poster_path !== null">
          <img
            class="poster_path poster_height w-100"
            :src="imageUrl + film.poster_path"
            :alt="film.name"
          />
        </div>
        <!-- immagine not found -->
        <div v-else>
          <img
            class="poster_path mt_90 w-100"
            src="@/assets/image-not-found.png"
            alt="not-found"
          />
        </div>
        <div class="card_text h-100 d-none">
          <ul class="list d-flex flex-column justify-content-center h-100">
            <!-- titolo -->
            <li><b>Titolo:</b> {{ film.title }}</li>
            <!-- titolo originale -->
            <li><b>Titolo originale:</b> {{ film.original_title }}</li>
            <!-- lingua -->
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
            <!-- voto -->
            <li v-if="film.vote_average > 0">
              <b>Voto:</b
              ><span
                v-for="(star, index) in intNumber(film.vote_average)"
                :key="index"
                ><i class="fa-solid fa-star yellow"></i
              ></span>
            </li>
            <li v-else><b>Voto: </b><span>0</span></li>
            <!-- trama -->
            <li v-if="film.overview.length > 0">
              <b>Trama: </b>{{ film.overview }}
            </li>
            <li v-else><b>Trama: </b>Non Disponibile</li>
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
  width: 342px;
  height: 515px;
  background-color: black;
  color: white;

  .poster_height {
    height: 515px;
  }

  .mt_90 {
    margin-top: 90px;
  }

  .card_text {
    font-size: 12px;

    .list {
      list-style-type: none;
      padding-inline-start: 3px;
      margin-left: 5px;

      .flag {
        width: 20px;
      }

      .yellow {
        color: yellow;
      }
    }
  }
}

.card:hover .card_text {
  display: inline !important;
}

.card:hover .poster_path {
  display: none !important;
}
</style>