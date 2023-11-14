<script>

import { store } from '../store';

export default {

  props: {
    item: {
      type: Object,
      required: true,
    },
  },

  data() {
    return {
      languages: ['it', 'en', 'de'],
      store,
    }
  },

  computed: {
    title() {
      return this.item.title ? this.item.title : this.item.name;
    },

    originalTitle() {
      return this.item.original_title ? this.item.original_title : this.item.original_name;
    },

    valutation() {
      return Math.ceil(this.item.vote_average / 2)
    }
  }
}

</script>

<template>
  <div class="movie-serie">

    <!-- Immagine di copertina -->
    <div class="film-image">
      <figure>
        <img v-if="item.poster_path" :src="'https://image.tmdb.org/t/p/w1280/' + item.poster_path" alt="">
        <img v-else src="https://www.avmagazine.it/immagini/netflix_frame_rate_4.jpg">
      </figure>
    </div>

    <!-- informazioni film -->
    <div class="informations">
      <div class="title">
        <p>Titolo : {{ title }}</p>
      </div>

      <div class="original-title" v-if="title !== originalTitle">
        <p>Titolo originale: {{ originalTitle }}</p>
      </div>

      <div class="language">

        <p v-if="languages.includes(item.original_language)">
          <img :src="'/public/Img/' + item.original_language + '.png'">
        </p>
        <p v-else>
          Lingua: {{ item.original_language }}
        </p>

      </div>

      <div class="rate">
        <!-- stelle piene -->
        <span>Voto: </span>

        <span v-for="star in valutation" :key="star">
          <font-awesome-icon icon="fa-solid fa-star" class="icon" />
        </span>

        <!-- stelle vuote -->
        <span v-for="star in 5 - valutation" :key="star">
          <font-awesome-icon icon="fa-regular fa-star" class="icon" />
        </span>

      </div>

      <div class="overview">
        <p>{{ item.overview }}</p>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
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
      flex-direction: column;
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

    .icon {
      color: yellow;
    }
  }

  &:hover .informations {
    display: flex;
    flex-direction: column;
    row-gap: 10px;
    overflow-y: scroll;
    padding: 10px;

    &::-webkit-scrollbar {
      display: none;
    }

  }
}
</style>