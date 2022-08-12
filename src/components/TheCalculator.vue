<template>
  <div class="wrapper">
    <div class="display">{{ display || 0 }}</div>
    <div class="btn" @click="clear">AC</div>
    <div class="btn" @click="sign">+/-</div>
    <div class="btn" @click="percent">%</div>
    <div class="btn operator" @click="divide">÷</div>
    <div class="btn" @click="append('7')">7</div>
    <div class="btn" @click="append('8')">8</div>
    <div class="btn" @click="append('9')">9</div>
    <div class="btn operator" @click="multiply">x</div>
    <div class="btn" @click="append('4')">4</div>
    <div class="btn" @click="append('5')">5</div>
    <div class="btn" @click="append('6')">6</div>
    <div class="btn operator" @click="minus">-</div>
    <div class="btn" @click="append('1')">1</div>
    <div class="btn" @click="append('2')">2</div>
    <div class="btn" @click="append('3')">3</div>
    <div class="btn operator" @click="plus">+</div>
    <div class="btn zero" @click="append('0')">0</div>
    <div class="btn zero" @click="appendPara()">( )</div>
    <div class="btn" @click="decimal">.</div>
    <div class="btn operator" @click="equal">=</div>
  </div>
</template>

<script>
export default {
  name: "TheCalculator",
  components: {},
  data() {
    return {
      display: "",
      operator: null,
      previous: null,
      operatorClicked: false,
    };
  },
  methods: {
    clear() {
      this.display = "";
    },
    sign() {
      this.display =
        this.display.charAt(0) === "-"
          ? this.display.slice(1)
          : `-${this.display}`;
    },
    percent() {
      this.display = `${parseFloat(this.display) / 100}`;
    },
    append(nbr) {
      if (this.operatorClicked) {
        this.display = "";
        this.operatorClicked = false;
      }
      this.display = `${this.display}${nbr}`;
    },
    appendPara() {
      if (this.operatorClicked) {
        this.display = "";
        this.operatorClicked = false;
      }
      this.display = `(${this.display})`;
    },
    decimal() {
      if (this.display.indexOf(".") === -1) {
        this.append(".");
      }
    },
    setPrevious() {
      this.previous = this.display;
      this.operatorClicked = true;
    },
    divide() {
      this.operator = (a, b) => a / b;
      this.setPrevious();
    },
    multiply() {
      this.operator = (a, b) => a * b;
      this.setPrevious();
    },
    minus() {
      this.operator = (a, b) => a - b;
      this.setPrevious();
    },
    plus() {
      this.operator = (a, b) => a + b;
      this.setPrevious();
    },
    equal() {
      this.display = `${this.operator(
        parseFloat(this.display),
        parseFloat(this.previous)
      )}`;
      this.previous = null;
    },
  },
};
</script>

<style scoped>
.wrapper {
  font-size: 25px;
  width: 500px;
  line-height: 90px;
  margin: auto;
  box-sizing: border-box;
  border: 5px solid black;
  border-radius: 5px;
  height: 500px;
  overflow: hidden;
  box-shadow: 3px 3px 3px #4b4b4c;
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-auto-rows: minmax(50px, auto);
}

.display {
  grid-column: 1 /5;
  background-color: white;
  text-align: end;
  padding-right: 10px;
  font-size: 40px;
}

.zero {
  /* grid-column: 1/3;
  margin: auto; */
}

.btn {
  background: #eeeeed;
  border: 1px solid #999;
}
.btn:hover,
.btn:active {
  background: white;
  /* color: #0e4f1f; */
}

.operator {
  background: #abd699;
  color: white;
}
</style>
