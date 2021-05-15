<template>
  <Sort />
</template>

<script>
import Sort from "./components/Sort.vue";

export default {
  name: "App",
  components: {
    Sort,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
