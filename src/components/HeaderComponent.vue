<template>
  <div class="container-fluid">
    <div class="row">
      <div class="col-6 p-3">
        <h1>BOOLFLIX</h1>
      </div>
      <div class="col-6 d-flex justify-content-end p-3">
        <input
          type="text"
          placeholder="Cerca"
          v-model="userText"
          class="me-2 m-2"
        />
        <button class="btn btn-sm m-2" @click="$emit('search', userText)">
          Cerca
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "HeaderComponent",
  data() {
    return {
      userText: "",
    };
  },
};
</script>

<style scoped lang="scss">
.row {
  background-color: black;

  h1 {
    font-size: 30px;
    color: rgb(168, 20, 20);
  }

  button {
    background-color: white;
  }
}
</style>