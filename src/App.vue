<template>
  <div class="nav">
    <h1>Coding Challenge</h1>
    <p>Jamar Riley</p>
  </div>
  <div class="button__row">
    <button class="button__counter" @click="activeBtn">
      Frequency Counter
    </button>
    <button class="button__calculator" @click="activeBtn">Calculator</button>
  </div>
  <mcv-frequency-component v-if="active"></mcv-frequency-component>
</template>

<script>
import mcvFrequencyComponent from "@/components/FrequencyComponent.vue";

export default {
  name: "App",
  components: {
    mcvFrequencyComponent,
  },
  data() {
    return {
      active: false,
    };
  },
  methods: {
    activeBtn() {
      this.active = !this.active;
    },
  },
};
</script>

<style>
.nav {
  text-align: center;
  font-size: large;

  background: #2ddf5c;
  padding: 0.1rem;
}

.button__row {
  display: flex;
  justify-content: center;
}

.button__counter {
  display: flex;
  margin: auto;
  margin-top: 1.5rem;
  background: #0c9ca6;
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
  color: #0e4f1f;
}
.button__calculator {
  display: flex;
  margin: auto;
  margin-top: 1.5rem;
  background: #0e4f1f;
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
  color: #0e4f1f;
}
</style>
