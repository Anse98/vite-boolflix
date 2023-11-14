<script >
import { store } from '../store.js';

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
  <header>
    <nav class="header-nav">
      <div class="title">
        <h1>BOOLFLIX</h1>
      </div>
      <div class="searchbar">
        <input type="search" placeholder="Cerca Film o serie tv" v-model.trim="store.searchValue"
          @keyup.enter="$emit('show')">
      </div>
    </nav>
  </header>
</template>

<style scoped lang="scss">
header {
  padding: 26px;
  background-color: black;

  .header-nav {
    display: flex;
    justify-content: space-between;
    align-items: center;

    .title {
      color: red;
    }

    .searchbar {


      input {
        padding: 8px;
        border: solid 3px red;
        border-radius: 6px;

      }
    }
  }
}
</style>
