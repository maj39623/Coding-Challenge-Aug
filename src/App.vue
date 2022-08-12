<template>
  <div class="nav">
    <h1>Coding Challenge</h1>
    <p>Jamar Riley</p>
  </div>
  <div class="button__row">
    <button class="button__counter" @click="activeBtn">
      Frequency Counter
    </button>
    <button class="button__calculator" @click="activeBtn2">Calculator</button>
  </div>
  <mcv-frequency-component v-if="active"></mcv-frequency-component>
  <calculator-component v-if="active2"></calculator-component>
</template>

<script>
import mcvFrequencyComponent from "@/components/FrequencyComponent.vue";
import CalculatorComponent from "@/components/CalculatorComponent.vue";

export default {
  name: "App",
  components: {
    mcvFrequencyComponent,
    CalculatorComponent,
  },
  data() {
    return {
      active: false,
      active2: false,
    };
  },
  methods: {
    activeBtn() {
      this.active = !this.active;
      if (this.active2 === true) {
        this.active2 = false;
      }
    },
    activeBtn2() {
      this.active2 = !this.active2;
      if (this.active === true) {
        this.active = false;
      }
    },
  },
};
</script>

<style>
body {
  margin: 0;
}

html {
  background-color: #fef9db;
}

.nav {
  text-align: center;
  font-size: large;
  color: white;
  background: #abd699;
  padding: 0.1rem;
  padding-left: 0%;
}

.button__row {
  display: flex;
  justify-content: center;
}

.button__counter {
  display: flex;
  margin: auto;
  margin-top: 1.5rem;
  background: #16123f;
  color: white;
  font: inherit;
  border: 1.5px solid #0e4f1f;
  padding: 0.5rem;
  border-radius: 8px;
  font-weight: normal;
  cursor: pointer;
}
.button__counter:hover,
.button__counter:active {
  background: white;
  color: #16123f;
}
.button__calculator {
  display: flex;
  margin: auto;
  margin-top: 1.5rem;
  background: #16123f;
  color: white;
  font: inherit;
  border: 1.5px solid #0e4f1f;
  padding: 0.5rem;
  border-radius: 8px;
  font-weight: normal;
  cursor: pointer;
}
.button__calculator:hover,
.button__calculator:active {
  background: white;
  color: #16123f;
}
</style>
