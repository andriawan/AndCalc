<template>
  <div class="row justify-content-md-center">
    <div class="col-md-auto">
      <div class="card">
        <div class="card-header">
          <h5 class="card-title">{{ app_title }} {{ app_version }}</h5>
          <p class="text-muted small mb-0">made with Vue.js</p>
        </div>
        <div class="card-body">
          <screen
            @on_screen_change="redefine"
            :external="display">
          </screen>
          <keypad 
            @key_set="setScreen"
            @on_operation="handleOperation"
            @on_result_set="setResult"
            @on_clear="clearScreen">
          </keypad>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Screen from "./Screen";
import Keypad from "./Keypad";

export default {
  name: "Content",
  props: ["app_title", "app_version"],
  components: {
    screen: Screen,
    keypad: Keypad
  },
  data() {
    return {
      display: "",
      operation: "",
      temp_data: "",
      result: "",
      banner: "Andriawan",
      website: "https://irwan.andriawan.com"
    };
  },
  methods: {
    setScreen(val) {
      if (this.result === null) {
      }
      this.result = this.result + val;
      this.display = this.result;
    },
    redefine(val) {
      this.result = val;
    },
    setResult() {
      if (this.result != null) {
        switch (this.operation) {
          case "multiple":
            this.result = this.result * this.temp_data;
            break;
          case "divide":
            this.result = this.temp_data / this.result;
            break;
          case "add":
            this.result = this.temp_data + parseFloat(this.result);
            break;
          case "subtract":
            this.result = this.temp_data - parseFloat(this.result);
            break;
          default:
            this.result = "";
        }

        this.updateDisplay(this.result);
        this.temp_data = parseFloat(this.result);
        this.result = "";
      }

      this.debug();
    },
    updateDisplay(data) {
      this.display = data;
    },
    debug() {
      console.log("-------- LOGGER ---------");
      console.log("operation " + this.operation);
      console.log("display " + this.display);
      console.log("result " + this.result);
      console.log("temp_data " + this.temp_data);
      console.log("-------- LOGGER ---------");
    },
    handleOperation(val) {
      this.operation = val;

      if (this.result === "") {
        return;
      } else {
        this.temp_data = parseFloat(this.result);
        this.result = "";
        this.debug();
      }
    },
    clearScreen() {
      this.display = "0";
      this.temp_data = 0;
      this.result = "";
    }
  },
  computed: {}
};
</script>

<style scoped>
.card-body {
  min-height: 300px;
}
</style>
