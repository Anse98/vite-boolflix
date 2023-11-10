<script >
import { store } from '../store';

export default {
  data() {
    return {
      store: store,
      languages: ['it', 'en', 'de']
    }
  },
  methods: {

  },
}
</script>

<template>
  <main>
    <div class="main-content">

      <!-- FILM -->
      <div class="movie-serie" v-for="movie in store.movies">

        <div class="title">
          <p>{{ movie.title }}</p>
        </div>

        <div class="original-title">
          <p>{{ movie.original_title }}</p>
        </div>

        <div class="language">

          <p v-if="languages.includes(movie.original_language)">
            <img :src="'/public/Img/' + movie.original_language + '.png'">
          </p>
          <p v-else>
            Lingua: {{ movie.original_language }}
          </p>
        </div>

        <div class="rate">
          <p>{{ movie.vote_average }}</p>
        </div>

        <div class="category">
          <p>Film</p>
        </div>
      </div>


      <!-- SERIE TV -->
      <div class="movie-serie" v-for="serie in store.series">

        <div class="title">
          <p>{{ serie.name }}</p>
        </div>

        <div class="original-title">
          <p>{{ serie.original_name }}</p>
        </div>

        <div class="language">

          <p v-if="languages.includes(serie.original_language)">
            <img :src="'/public/Img/' + serie.original_language + '.png'">
          </p>
          <p v-else>
            Lingua: {{ serie.original_language }}
          </p>
        </div>

        <div class="rate">
          <p>{{ serie.vote_average }}</p>
        </div>

        <div class="category">
          <p>Serie TV</p>
        </div>
      </div>
    </div>
  </main>
</template>

<style scoped lang="scss">
main {
  background-color: gray;
  flex-grow: 1;

  .movie-serie {
    border: solid 1px black;
    padding: 20px;

    .language {

      img {
        max-width: 30px;
      }
    }
  }
}
</style>