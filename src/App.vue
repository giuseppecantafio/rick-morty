<template>
  <div id="app">
  
    <HeaderComponent :title="titolo"/> 
    <!-- se è un valore primitivo non sevono i : -->
    <main>
      <GridComponent />
    </main>
    <LoaderComponent />
  </div>
</template>

<script>
import HeaderComponent from './components/HeaderComponent.vue';
import GridComponent from './components/GridComponent.vue';
import LoaderComponent from './components/LoaderComponent.vue';

export default {
  name: 'App',
  components: {
    HeaderComponent,
    GridComponent,
    LoaderComponent,
  },
  data() {
    return {
      titolo: 'Rick e Morty',
    }
  }
}
</script>

<style lang="scss">
@import "@/style/general.scss";
</style>
