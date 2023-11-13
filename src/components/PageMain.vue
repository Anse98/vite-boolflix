<script >
import { store } from '../store';


export default {
  data() {
    return {
      store: store,
      languages: ['it', 'en', 'de'],
    }
  },
  methods: {

  },

  components: {

  },

  computed: {
    vote() {
      return Math.ceil(this.store.movies.vote_average / 2)
    }
  }

}
</script>

<template>
  <main>
    <div class="main-content">

      <!-- FILM -->
      <div class="container">

        <div class="row">

          <div class="movie-serie" v-for="movie in store.movies">

            <!-- Immagine di copertina -->
            <div class="film-image">
              <figure>
                <img :src="'https://image.tmdb.org/t/p/w1280/' + movie.poster_path"
                  alt=" Nessuna immagine di copertina disponibile">
              </figure>
            </div>

            <!-- informazioni film -->
            <div class="informations">
              <div class="title">
                <p>Titolo : {{ movie.title }}</p>
              </div>

              <div class="original-title">
                <p>Titolo originale: {{ movie.original_title }}</p>
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
                <!-- stelle piene -->
                <span>Voto: </span>
                <span v-for="star in Math.ceil(movie.vote_average / 2)
                ">
                  <font-awesome-icon icon="fa-solid fa-star" />
                </span>
                <!-- stelle vuote -->
                <span v-for="star in 5 - Math.ceil(movie.vote_average / 2)
                ">
                  <font-awesome-icon icon="fa-regular fa-star" />
                </span>

              </div>

              <div class="category">
                <p> Categoria: Film</p>
              </div>
            </div>
          </div>

          <!-- SERIE TV -->
          <div class="movie-serie del" v-for="serie in store.series">

            <!-- Immagine di copertina -->
            <div class="serie-image">
              <figure>
                <img :src="'https://image.tmdb.org/t/p/w1280/' + serie.poster_path"
                  alt=" Nessuna immagine di copertina disponibile">
              </figure>
            </div>

            <!-- Informazioni serie -->
            <div class="informations">
              <div class="title">
                <p>Titolo: {{ serie.name }}</p>
              </div>

              <div class="original-title">
                <p>Titolo originale: {{ serie.original_name }}</p>
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
                <!-- stelle piene -->
                <span>Voto: </span>
                <span v-for="star in Math.ceil(serie.vote_average / 2)
              ">
                  <font-awesome-icon icon="fa-solid fa-star" />
                </span>
                <!-- stelle vuote -->
                <span v-for="star in 5 - Math.ceil(serie.vote_average / 2)
              ">
                  <font-awesome-icon icon="fa-regular fa-star" />
                </span>

              </div>

              <div class="category">
                <p>Categoria: Serie TV</p>
              </div>
            </div>
          </div>
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

  .movie-serie {

    padding: 10px;
    display: flex;
    align-items: center;
    flex-direction: column;
    position: relative;

    .film-image,
    .serie-image {


      figure {
        max-width: 200px;
        border: solid 2px lightgray;
        display: flex;
        justify-content: center;
      }
    }

    .language {
      img {
        max-width: 30px;
      }
    }

    .informations {
      position: absolute;
      background-color: black;
      color: white;
      top: 0;
      bottom: 0;
      left: 0;
      right: 0;
      border: solid 2px lightgray;
      padding: 10px;
      display: none;
    }

    &:hover .informations {
      display: flex;
      flex-direction: column;
      row-gap: 20px;
      justify-content: center;
      align-items: center;
      text-align: center;
    }
  }
}
</style>