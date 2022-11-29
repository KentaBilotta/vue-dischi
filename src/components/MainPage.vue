<template>
  <div class="col-8">
    <div class="row row-cols-5">
    <CardPage
      v-for="album in arrDati"
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
