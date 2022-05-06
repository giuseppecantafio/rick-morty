<template>
  <section class="container">
    <div class="row">
      <loader-component v-if="loading" />
      <div
        class="col-6 col-md-4 col-lg-3"
        v-for="character in characterList"
        :key="character.id"
      >
        <card-component :item="character" />
      </div>
    </div>
    <footer-component :lng="characterList.length"/>
  </section>
</template>

<script>
import LoaderComponent from "./LoaderComponent.vue";
import CardComponent from "./CardComponent.vue";
import FooterComponent from './FooterComponent.vue';
import axios from "axios";

export default {
  components: { LoaderComponent, CardComponent, FooterComponent },
  name: "GridComponent",
  data() {
    return {
      characterList: [],
      apiPath: "https://api.sampleapis.com/rickandmorty/",
      loading: false,
    };
  },
  mounted() {
    this.loading = true;
    axios
      .get(this.apiPath + "characters")
      .then((res) => {
        this.characterList = [...res.data];
        console.log(this.characterList);
        this.loading = false;
      })
      .catch((error) => {
        console.log(error);
        this.loading = false;
      });
  },
};
</script>

<style lang="scss" scoped></style>
