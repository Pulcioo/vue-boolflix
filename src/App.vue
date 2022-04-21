<template>
  <div id="app">
    <HeaderComponent @search="searchApi" />
    <MainComponent :films="films" :series="series" />
  </div>
</template>

<script>
import MainComponent from "./components/MainComponent.vue";
import HeaderComponent from "./components/HeaderComponent.vue";
import axios from "axios";

export default {
  name: "App",
  components: {
    HeaderComponent,
    MainComponent,
  },
  data() {
    return {
      apiUrl: "https://api.themoviedb.org/3/search/",
      apiKey: "921ca470afccdb8fe8422b187e30bb97",
      films: [],
      series: [],
    };
  },
  methods: {
    searchApi(userText) {
      if (userText.length > 0) {
        const params = {
          query: userText,
          api_key: this.apiKey,
          language: "it-IT",
        };
        axios // chiamata Api per movies
          .get(this.apiUrl + "movie", { params })
          .then((response) => {
            // console.log(response);
            this.films = response.data.results;
            console.log(this.films);
          })
          .catch((error) => {
            console.log(error);
          });

        axios // chiamata Api per series
          .get(this.apiUrl + "tv", { params })
          .then((response) => {
            // console.log(response);
            this.series = response.data.results;
            console.log(this.series);
          })
          .catch((error) => {
            console.log(error);
          });
      }
    },
  },
};
</script>

<style lang="scss">
@import "@/style/general";
</style>
