<template>
  <div class="input-group">
    <input
      type="text"
      class="form-control"
      placeholder="Cerca nei personaggi"
      aria-label="Recipient's username"
      aria-describedby="basic-addon2"
      v-model="inputText"
      @keyup.enter="search"
    />
    <div class="input-group-append">
      <button class="btn btn-outline-secondary" type="button" @click="search">
        Cerca
      </button>
      <button class="btn btn-outline-secondary" type="button" @click="reset">
        Reset
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: "SearchComponent",
  data() {
    return {
      inputText: "",
    };
  },
  methods: {
    reset() {
      this.$emit("mySearch", this.inputText);
      this.inputText = "";
    },
    search() {
      this.$emit("mySearch", this.inputText);
      this.inputText = "";
    },
  },
};
</script>

<style lang="scss" scoped></style>
