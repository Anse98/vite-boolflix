<script>
import PageHeader from './components/PageHeader.vue';
import PageMain from './components/PageMain.vue';
import axios from 'axios';
import { store } from './store';

export default {
  components: {
    PageHeader,
    PageMain,
  },

  methods: {
    showMoviesSeries() {
      axios.get(`${this.moviesUrl}?api_key=${this.API_KEY}&query=${this.store.searchValue}`).then(res => {
        this.store.movies = res.data.results;
      })

      axios.get(`${this.seriesUrl}?api_key=${this.API_KEY}&query=${this.store.searchValue}`).then(res => {
        this.store.series = res.data.results;
      })
    }
  },

  data() {
    return {
      store: store,
      moviesUrl: 'https://api.themoviedb.org/3/search/movie',
      API_KEY: store.API_KEY,
      seriesUrl: 'https://api.themoviedb.org/3/search/tv',
    }
  },

  mounted() {

  }
}
</script>

<template>
  <PageHeader @show="showMoviesSeries" />
  <PageMain />
</template>

<style lang="scss">
@use './styles/general.scss';
</style>
