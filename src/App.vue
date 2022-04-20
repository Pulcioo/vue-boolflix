<template>
  <div id="app">
    <HeaderComponent @search="searchApi" />
    <MainComponent />
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
      arrayFilm: [],
    };
  },
  methods: {
    searchApi(userText) {
      const params = {
        query: userText,
        api_key: this.apiKey,
        language: "it-IT",
      };
      axios
        .get(this.apiUrl + "movie", { params })
        .then((response) => {
          console.log(response);
        })
        .catch((error) => {
          console.log(error);
        });
    },
  },
};
</script>

<style lang="scss">
@import "@/style/general";
</style>
