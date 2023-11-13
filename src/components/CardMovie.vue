<script>

export default {

  props: {
    item: {
      type: Object,
      required: true,
    },

    cardType: {
      type: String,
      required: true,
    }
  },

  data() {
    return {
      languages: ['it', 'en', 'de'],
    }
  },

  computed: {
    title() {
      return (this.cardType === 'movie') ? this.item.title : this.item.name;
    },

    originalTitle() {
      return (this.cardType === 'movie') ? this.item.original_title : this.item.original_name;
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
        <img :src="'https://image.tmdb.org/t/p/w1280/' + item.poster_path"
          alt=" Nessuna immagine di copertina disponibile">
      </figure>
    </div>

    <!-- informazioni film -->
    <div class="informations">
      <div class="title">
        <p>Titolo : {{ title }}</p>
      </div>

      <div class="original-title">
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

        <span v-for="star in valutation">
          <font-awesome-icon icon="fa-solid fa-star" />
        </span>

        <!-- stelle vuote -->
        <span v-for="star in 5 - valutation">
          <font-awesome-icon icon="fa-regular fa-star" />
        </span>

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
</style>