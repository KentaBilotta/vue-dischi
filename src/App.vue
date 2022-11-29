<template>
  <div class="cont d-flex justify-content-center align-items-center">
    <MainPage />
  </div>
</template>

<script>
import MainPage from '@/components/MainPage.vue';

export default {
  components: {
    MainPage,
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
