<template>
  <div class="col-8">
    <div class="row row-cols-5">
    <CardPage
      v-for="album in arrAlbumsFiltered"
      :key="album.title"
      :posterUrl="album.poster"
      :title="album.title"
      :author="album.author"
      :year="album.year"
    />
  </div>
  </div>
</template>

<script>
import CardPage from '@/components/CardPage.vue';
import axios from 'axios';

export default {
  name: 'MainPage',
  components: {
    CardPage,
  },
  data() {
    return {
      arrDati: null,
      urlApi: 'https://flynn.boolean.careers/exercises/api/array/music',
    };
  },
  props: {
    genreFilter: String,
  },
  computed: {
    arrGenres() {
      const arrGenres = [];
      if (this.arrDati) {
        this.arrDati.forEach((objAlbum) => {
          if (!arrGenres.includes(objAlbum.genre)) {
            arrGenres.push(objAlbum.genre);
          }
        });
      }
      // console.log(arrGenres);
      return arrGenres;
    },
    arrAlbumsFiltered() {
      if (this.genreFilter === 'All') {
        return this.arrDati;
      }
      return this.arrDati.filter((objAlbum) => objAlbum.genre === this.genreFilter);
    },
  },
  watch: {
    arrGenres(newValue, oldValue) {
      console.log(newValue, oldValue);
      this.$emit('genresReady', newValue);
    },
  },
  created() {
    axios.get(this.urlApi)
      .then((axiosResponse) => {
        console.log(axiosResponse);
        this.arrDati = axiosResponse.data.response;
        console.log(this.arrDati);
      });
  },
};
</script>

<style lang="scss">

</style>
