<script >
import { store } from '../store';

export default {
  data() {
    return {
      store: store,
    }
  },
  methods: {

  },
}
</script>

<template>
  <main>
    <div class="main-content">
      <!-- informazioni film -->
      <div class="movie" v-for="movie in store.movies">
        <div class="title">
          <p>{{ movie.title }}</p>
        </div>
        <div class="original-title">
          <p>{{ movie.original_title }}</p>
        </div>
        <div class="language">

          <p v-if="movie.original_language === 'it'">
            <img src="/public/Img/1200px-Bandiera_italiana_foto.svg.png">
          </p>
          <p v-else-if="movie.original_language === 'en'">
            <img src="/public/Img/Gran-Bretagna.jpg">
          </p>
          <p v-else-if="movie.original_language === 'de'">
            <img src="/public/Img/Flag_of_Germany.svg.png">
          </p>
          <p v-else>
            {{ movie.original_language }}
          </p>
        </div>

        <div class="rate">
          <p>{{ movie.vote_average }}</p>
        </div>
      </div>
      <div>

      </div>
    </div>
  </main>
</template>

<style scoped lang="scss">
main {
  background-color: gray;
  flex-grow: 1;

  .movie {
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