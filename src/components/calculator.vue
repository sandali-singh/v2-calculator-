<template>
  <div
    class="p-4 rounded-5"
    style="max-width: 400px; margin: 50px auto; background: #234"
  >
    <h1 class="text-white p-3 text-center">Calculator</h1>
    <!--Result-->
    <div
      class="w-full rounded text-left m-1 p-3 lead font-weight-bold text-white bg-vue-dark"
    >
      {{ calculatorValue || 0 }}
    </div>
    <!-- Buttons (0-9)-->
    <div class="row no-gutters">
      <div class="col-3" v-for="n in calculatorNums" :key="n">
        <div
          class="lead text-white text-center m-1 py-3 bg-vue-dark rounded hover-class"
          :class="{
            'bg-vue-solid': ['c', '*', '/', '-', '+', '%', '='].includes(n),
          }"
          @click="action(n)"
        >
          {{ n }}
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "my-calculator",
  data() {
    return {
      calculatorValue: "",
      calculatorNums: [
        "c",
        "*",
        "/",
        "%",
        1,
        2,
        3,
        "+",
        4,
        5,
        6,
        "-",
        7,
        8,
        9,
        "=",
        0,
        ".",
      ],
      oprator: null,
      previousCalculatorValue: "",
    };
  },
  methods: {
    action(n) {
      if (!isNaN(n) || n === ".") {
        this.calculatorValue += n + "";
      }
      /* clearing value */
      if (n === "c") {
        this.calculatorValue = "";
      }
      /* percentage */
      if (n === "%") {
        this.calculatorValue = this.calculatorValue / 100 + "";
      }
      if (["/", "*", "-", "+"].includes(n)) {
        this.oprator = n;
        this.previousCalculatorValue = this.calculatorValue;
        this.calculatorValue = "";
      }

      if (n === "=") {
        this.calculatorValue = eval(
          this.previousCalculatorValue + this.oprator + this.calculatorValue
        );
        this.previousCalculatorValue = "";
        this.oprator = null;
      }
    },
  },
};
</script>

<style scoped>
.bg-vue-dark {
  background: #85586f;
}
.hover-class:hover {
  cursor: pointer;
  background: #3d5875;
}
.bg-vue-solid {
  background: #ac7d88;
}
</style>
