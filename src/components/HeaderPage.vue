<template>
  <div class="head-cont d-flex justify-content-around align-items-center">
    <h3 class="text-white">Vue Dischi</h3>
    <label for="select">
      <select
        id="select"
        name="genres"
        class="p-1 rounded"
        @change="genreChange"
        v-model="genreFilter"
      >
        <option value="All">All</option>
        <option
          v-for="genre in genresList"
          :key="genre"
          :value="genre"
        >
          {{ genre }}
        </option>
      </select>
    </label>
  </div>
</template>

<script>
export default {
  name: 'HeaderPage',
  props: {
    genresList: Array,
  },
  data() {
    return {
      genreFilter: 'All',
    };
  },
  methods: {
    genreChange() {
      this.$emit('changedGenre', this.genreFilter);
    },
  },
};
</script>

<style lang="scss">
  .head-cont{
    background-color: #2e3a46;
    width: 100%;
    height: 8vh;
  }

</style>
