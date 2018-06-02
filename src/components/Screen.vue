<template>
    <div class="form-group">
      <input 
        :value="external"
        type="number" 
        class="form-control form-control-lg"
        id="exampleInputEmail1" 
        aria-describedby="emailHelp"
        @keyup="redefine($event.target.value)"
      >
    </div>
</template>

<script>
export default {
  name: "Screen",
  props: ["external"],
  data() {
    return {};
  },
  methods: {
    redefine(data) {
      this.$emit("on_screen_change", data);
    }
  }
};
</script>
