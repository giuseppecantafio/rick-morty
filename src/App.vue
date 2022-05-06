<template>
  <div id="app">
  
    <HeaderComponent :title="titolo"/> 
    <!-- se è un valore primitivo non sevono i : -->
    <main>
      <GridComponent />
    </main>
  </div>
</template>

<script>
import HeaderComponent from './components/HeaderComponent.vue';
import GridComponent from './components/GridComponent.vue';

export default {
  name: 'App',
  components: {
    HeaderComponent,
    GridComponent,
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
