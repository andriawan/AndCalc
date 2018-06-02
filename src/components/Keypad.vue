<template>
  <div class="container">
    <div class="row">
      <div class="col operation">
        <a class="operation" @click="operation('multiple')">
          <div :class="[operationStyle, multipleStyle]" role="alert">
            x
          </div>
        </a>
      </div>
      <div class="col operation">
        <a class="operation" @click="operation('divide')">
          <div :class="[operationStyle, divideStyle]" role="alert">
            /
          </div>
        </a>
      </div>
      <div class="col operation">
        <a class="operation" @click="operation('add')">
          <div :class="[operationStyle, addStyle]" role="alert">
            +
          </div>
        </a>
      </div>
      <div class="col operation">
        <a class="operation" @click="operation('subtract')">
          <div :class="[operationStyle, subtractStyle]" role="alert">
            -
          </div>
        </a>
      </div>
    </div>
    <div class="row">
      <div class="col">
        <a class="operation" @click="setKey(1)">
          <div class="alert alert-dark push" role="alert">
            1
          </div>
        </a>
      </div>
      <div class="col">
        <a class="operation" @click="setKey(2)">
          <div class="alert alert-dark push" role="alert">
            2
          </div>
        </a>
      </div>
      <div class="col">
        <a class="operation" @click="setKey(3)">
          <div class="alert alert-dark push" role="alert">
            3
          </div>
        </a>
      </div>
    </div>
    <div class="row">
      <div class="col">
        <a class="operation" @click="setKey(4)">
          <div class="alert alert-dark push" role="alert">
            4
          </div>
        </a>
      </div>
      <div class="col">
        <a class="operation" @click="setKey(5)">
          <div class="alert alert-dark push" role="alert">
            5
          </div>
        </a>
      </div>
      <div class="col">
        <a class="operation" @click="setKey(6)">
          <div class="alert alert-dark push" role="alert">
            6
          </div>
        </a>
      </div>
    </div>
    <div class="row">
      <div class="col">
        <a class="operation" @click="setKey(7)">
          <div class="alert alert-dark push" role="alert">
            7
          </div>
        </a>
      </div>
      <div class="col">
        <a class="operation" @click="setKey(8)">
          <div class="alert alert-dark push" role="alert">
            8
          </div>
        </a>
      </div>
      <div class="col">
        <a class="operation" @click="setKey(9)">
          <div class="alert alert-dark push" role="alert">
            9
          </div>
        </a>
      </div>
    </div>
    <div class="row">
      <div class="col">
        <a class="operation" @click="setKey(0)">
          <div class="alert alert-dark push" role="alert">
            0
          </div>
        </a>
      </div>
    </div>
    <div class="row">
      <div class="col">
        <a class="operation" @click="setResult">
          <div class="alert alert-dark push" role="alert">
            =
          </div>
        </a>
      </div>
      <div class="col">
        <a class="operation" @click="clear">
          <div class="alert alert-dark push" role="alert">
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
      },
      operationStyle: {
        alert: true,
        "alert-dark": true
      },
      multipleStyle: {
        active_multiple: false
      },
      divideStyle: {
        active_divide: false
      },
      addStyle: {
        active_add: false
      },
      subtractStyle: {
        active_subtract: false
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
        this.clearStyleOperation();
        this.multipleStyle.active_multiple = true;
        console.log("[LOG i: doing multiple]");
      } else if (val === "divide") {
        this.$emit("on_operation", "divide");
        this.clearStyleOperation();
        this.divideStyle.active_divide = true;
        console.log("[LOG i: doing divide]");
      } else if (val === "add") {
        this.$emit("on_operation", "add");
        this.clearStyleOperation();
        this.addStyle.active_add = true;
        console.log("[LOG i: doing add]");
      } else if (val === "subtract") {
        this.$emit("on_operation", "subtract");
        this.clearStyleOperation();
        this.subtractStyle.active_subtract = true;
        console.log("[LOG i: doing subtract]");
      }
    },
    clear() {
      this.clearStyleOperation();
      this.$emit("on_clear");
    },
    clearStyleOperation() {
      this.addStyle.active_add = false;
      this.multipleStyle.active_multiple = false;
      this.divideStyle.active_divide = false;
      this.subtractStyle.active_subtract = false;
    }
  }
};
</script>

<style scoped>
a.operation {
  cursor: -webkit-grabbing;
}

.alert.alert-dark.push:hover {
  background: #929495;
}

.active_multiple,
.active_add,
.active_subtract,
.active_divide {
  background: #929495;
}
</style>
