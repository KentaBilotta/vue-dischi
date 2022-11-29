<template>
  <div class="col p-2 text-center">
    <div class="contents d-flex flex-column align-items-center p-3">
      <div class="img">
        <img :src="posterUrl" :alt="title">
      </div>
      <div class="text-white p-1 text-uppercase fs-5">{{ title }}</div>
      <div class="author text-secondary">{{ author }}</div>
      <div class="publish-year text-secondary">{{ year }}</div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CardPage',
  props: {
    posterUrl: String,
    title: String,
    author: String,
    year: String,
  },
};
</script>

<style lang="scss" scoped>
.img{
  width: 100%;
  height: 150px;
  background-color: transparent;
  img{
    width: 100%;
    height: 100%;
    object-fit: cover;
  }
}
.contents{
  background-color: #2e3a46;
  height: 100%;
}

</style>
