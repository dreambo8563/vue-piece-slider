<template>
  <div class="content" id="app">
    <Slider :list="list" v-model="activeIndex"></Slider>
  </div>
</template>

<script>
import Slider from "./index.vue";

export default {
  name: "app",
  data() {
    return {
      activeIndex: 0,
      list: [
        "/img/1.jpg",
        "/img/2.jpg",
        "/img/3.jpg",
        "/img/4.jpg",
        "/img/5.jpg"
      ]
    };
  },
  components: {
    Slider
  }
};
</script>

<style lang="scss">
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
