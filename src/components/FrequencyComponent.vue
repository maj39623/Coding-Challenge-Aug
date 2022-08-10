<template>
  <div class="form">
    <h1>Character Frequency</h1>
    <form @submit.prevent>
      <textarea
        placeholder="Enter your text here..."
        class="center"
        name="string"
        cols="50"
        rows="10"
        v-model="str"
      ></textarea>
    </form>
    <button @click="algo(str)" class="button">Submit</button>

    <div class="form">
      <h2>Results</h2>
      <p>{{ result }}</p>
      <ol>
        <li v-for="char in sliced" :key="char">{{ char[0] }}: {{ char[1] }}</li>
      </ol>
    </div>
  </div>
</template>

<script>
export default {
  name: "mcvFrequencyComponent",
  data() {
    return {
      result: "",
      sliced: [],
      str: "",
    };
  },
  methods: {
    algo(str) {
      let string = str.replace(/\s/g, "");
      const charMap = {};
      let max = 0;
      let maxChar = "";
      let top = [];

      for (let char of string) {
        if (charMap[char]) {
          charMap[char]++;
        } else {
          charMap[char] = 1;
        }
      }
      for (let char in charMap) {
        top.push([char, charMap[char]]);

        if (charMap[char] > max) {
          max = charMap[char];
          maxChar = char;
        }
      }
      top.sort(function (a, b) {
        return b[1] - a[1];
      });

      this.sliced = top.slice(0, 10);
      console.log(this.sliced);
      this.result =
        "The Top Letter is " +
        maxChar.toUpperCase() +
        ". " +
        "for a count of " +
        max;
    },
  },
};
</script>

<style>
h1 {
  color: blue;
  text-align: center;
}

h2 {
  color: rgb(7, 17, 14);
  text-align: center;
}

.form {
  margin: auto;
  width: 50%;
  /* border: 3px solid green; */
  padding: 10px;
}

.center {
  display: block;
  margin: auto;
}

.button {
  display: block;
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
.button:hover,
.button:active {
  background: white;
  color: #0e4f1f;
}

li {
  padding: 0.5rem;
}
</style>
