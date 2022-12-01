<template>
  <div>
    <HeaderPage :genres-list="genresList" @changedGenre="genreChange" />
    <div class="cont d-flex flex-column justify-content-center align-items-center">
      <MainPage :genre-filter="genreFilter" @genresReady="getGenresList" />
    </div>
  </div>
</template>

<script>
import MainPage from '@/components/MainPage.vue';
import HeaderPage from '@/components/HeaderPage.vue';

export default {
  components: {
    MainPage,
    HeaderPage,
  },
  data() {
    return {
      genresList: [],
      genreFilter: 'All',
    };
  },
  methods: {
    getGenresList(genresList) {
      this.genresList = genresList;
    },
    genreChange(genreFilter) {
      this.genreFilter = genreFilter;
    },
  },
};
</script>

<style lang="scss">
@import "../node_modules/bootstrap/scss/bootstrap";

body{
  background-color: #1e2d3b;
}

.cont{
  height: 100vh;
}

</style>
