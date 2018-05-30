<template>
  <div class="row justify-content-md-center">
    <div class="col-md-auto">
      <div class="card">
        <div class="card-header">
          <h5 class="card-title">{{ app_title }} {{ app_version }}</h5>
        </div>
        <div class="card-body">
          <screen/>
          <keypad/>
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
      banner: "Andriawan",
      website: "https://irwan.andriawan.com"
    };
  }
};
</script>

<style scoped>
.card-body {
  height: 300px;
}
</style>
