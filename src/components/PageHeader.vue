<script >
import { store } from '../store.js';

export default {
  data() {
    return {
      store: store,
    }
  },
}
</script>

<template>
  <header>
    <nav class="header-nav">
      <div class="title">
        <h1>BOOLFLIX</h1>
      </div>
      <div>
        <input type="search" placeholder="Cerca Film o serie tv">
        <button>Cerca</button>
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

    input {
      padding-left: 10px;
    }
  }
}
</style>
