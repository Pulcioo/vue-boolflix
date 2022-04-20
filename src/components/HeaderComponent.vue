<template>
  <div class="container-fluid">
    <div class="row">
      <div class="col-6 p-3">BOOLFLIX</div>
      <div class="col-6 d-flex justify-content-end p-3">
        <input
          type="text"
          placeholder="Cerca"
          v-model="userText"
          class="me-2"
        />
        <button class="btn btn-sm" @click="$emit('search', userText)">
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
</style>