<template>
  <div class="app">
    <h1 class="title">Calculator</h1>
    <the-calculator></the-calculator>
  </div>
</template>

<script>
import TheCalculator from "@/components/TheCalculator.vue";

export default {
  name: "CalculatorComponent",
  components: {
    TheCalculator,
  },
};
</script>

<style scoped>
.app {
  text-align: center;
  margin-top: 60px;
}

.title {
  font-size: 2rem;
  color: #16123f;
}
</style>
