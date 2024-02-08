<template>
  <div id="app">
    <calculator></calculator>
  </div>
</template>

<script>
import calculator from "./components/calculator.vue";
export default {
  name: "app",
  components: {
    calculator,
  },
};
</script>

<style scoped>
#app {
}
</style>
