<script >
import { store } from '../store';
import Card from './CardMovie.vue';


export default {
  data() {
    return {
      store: store,
    }
  },

  methods: {

  },

  components: {
    Card,
  }

}
</script>

<template>
  <main>
    <div class="main-content">


      <div class="container">

        <div class="row">

          <!-- FILM -->
          <Card v-for="movie in store.movies" :item="movie" />

          <!-- SERIE TV -->
          <Card v-for="serie in store.series" :item="serie" />

        </div>
      </div>
    </div>
  </main>
</template>

<style scoped lang="scss">
main {
  background-color: gray;
  flex-grow: 1;
  padding-top: 50px;
}
</style>