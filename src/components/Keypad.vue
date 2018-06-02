<template>
  <div class="container">
    <div class="row">
      <div class="col operation">
        <a class="operation" @click="operation('multiple')">
          <div class="alert alert-dark" role="alert">
            x
          </div>
        </a>
      </div>
      <div class="col operation">
        <a class="operation" @click="operation('divide')">
          <div class="alert alert-dark" role="alert">
            /
          </div>
        </a>
      </div>
      <div class="col operation">
        <a class="operation" @click="operation('add')">
          <div class="alert alert-dark" role="alert">
            +
          </div>
        </a>
      </div>
      <div class="col operation">
        <a class="operation" @click="operation('subtract')">
          <div class="alert alert-dark" role="alert">
            -
          </div>
        </a>
      </div>
    </div>
    <div class="row">
      <div class="col">
        <a @click="setKey(1)">
          <div class="alert alert-dark" role="alert">
            1
          </div>
        </a>
      </div>
      <div class="col">
        <a @click="setKey(2)">
          <div class="alert alert-dark" role="alert">
            2
          </div>
        </a>
      </div>
      <div class="col">
        <a @click="setKey(3)">
          <div class="alert alert-dark" role="alert">
            3
          </div>
        </a>
      </div>
    </div>
    <div class="row">
      <div class="col">
        <a @click="setKey(4)">
          <div class="alert alert-dark" role="alert">
            4
          </div>
        </a>
      </div>
      <div class="col">
        <a @click="setKey(5)">
          <div class="alert alert-dark" role="alert">
            5
          </div>
        </a>
      </div>
      <div class="col">
        <a @click="setKey(6)">
          <div class="alert alert-dark" role="alert">
            6
          </div>
        </a>
      </div>
    </div>
    <div class="row">
      <div class="col">
        <a @click="setKey(7)">
          <div class="alert alert-dark" role="alert">
            7
          </div>
        </a>
      </div>
      <div class="col">
        <a @click="setKey(8)">
          <div class="alert alert-dark" role="alert">
            8
          </div>
        </a>
      </div>
      <div class="col">
        <a @click="setKey(9)">
          <div class="alert alert-dark" role="alert">
            9
          </div>
        </a>
      </div>
    </div>
    <div class="row">
      <div class="col">
        <a @click="setKey(0)">
          <div class="alert alert-dark" role="alert">
            0
          </div>
        </a>
      </div>
    </div>
    <div class="row">
      <div class="col">
        <a @click="setResult">
          <div class="alert alert-dark" role="alert">
            =
          </div>
        </a>
      </div>
      <div class="col">
        <a @click="clear">
          <div class="alert alert-dark" role="alert">
            C
          </div>
        </a>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Keypad",
  data() {
    return {
      config: {
        row: 3,
        digit: 9
      }
    };
  },
  methods: {
    setKey(value) {
      this.$emit("key_set", value);
    },
    setResult() {
      this.$emit("on_result_set");
    },
    operation(val) {
      if (val === "multiple") {
        this.$emit("on_operation", "multiple");
        console.log("[LOG i: doing multiple]");
      } else if (val === "divide") {
        this.$emit("on_operation", "divide");
        console.log("[LOG i: doing divide]");
      } else if (val === "add") {
        this.$emit("on_operation", "add");
        console.log("[LOG i: doing add]");
      } else if (val === "subtract") {
        this.$emit("on_operation", "subtract");
        console.log("[LOG i: doing subtract]");
      }
    },
    clear() {
      this.$emit("on_clear");
    }
  }
};
</script>

<style>
a.operation {
  cursor: -webkit-grabbing;
}
</style>
