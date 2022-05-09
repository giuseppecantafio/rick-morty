<template>
  <section class="container">
    <search-component @mySearch="setSearchText($event)" />
    <div class="row">
      <loader-component v-if="loading" />
      <div
        class="col-6 col-md-4 col-lg-3"
        v-for="character in filteredList"
        :key="character.id"
      >
        <card-component :item="character" />
      </div>
    </div>
    <footer-component :lng="filteredList.length" v-if="!loading" />
  </section>
</template>

<script>
import LoaderComponent from "./LoaderComponent.vue";
import CardComponent from "./CardComponent.vue";
import FooterComponent from "./FooterComponent.vue";
import SearchComponent from "./SearchComponent.vue";
import axios from "axios";

export default {
  components: {
    LoaderComponent,
    CardComponent,
    FooterComponent,
    SearchComponent,
  },
  name: "GridComponent",
  data() {
    return {
      characterList: [],
      searchText: "",
      apiPath: "https://api.sampleapis.com/rickandmorty/",
      loading: false,
    };
  },
  methods: {
    setSearchText(text) {
      this.searchText = text;
    },
  },
  computed: {
    filteredList() {
      // PER EVITARE DI FARGLIELO FARE SEMPRE METTO QUESTO CONTROLLO
      if (this.searchText === "") return this.characterList;
      // SE C'è UNA RICERCA LANCIA INVECE QUESTO
      return this.characterList.filter((element) => {
        if (
          element.name.toLowerCase().includes(this.searchText.toLowerCase())
        ) {
          return true;
        } else {
          return false;
        }
      });
    },
  },
  mounted() {
    this.loading = true;
    axios
      .get(this.apiPath + "characters")
      .then((res) => {
        this.characterList = [...res.data];
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
