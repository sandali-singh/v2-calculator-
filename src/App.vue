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
body {
  background: #643843;
}
</style>
