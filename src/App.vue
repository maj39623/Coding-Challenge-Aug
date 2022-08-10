<template>
  <h1 class="nav">Coding Challenge</h1>
  <p>Jamar Riley</p>
  <button class="button__nav" @click="activeBtn">Frequency Counter</button>
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
  width: 100%;
  text-align: center;
  font-size: x-large;

  background: #2ddf5c;
  padding: 1.5rem 1rem;
  position: relative;
}

.button__nav {
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
.button__nav:hover,
.button__nav:active {
  background: white;
  color: #0e4f1f;
}
</style>
