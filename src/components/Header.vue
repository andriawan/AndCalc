<template>
  <div class="hello">
    <h1>{{ banner }}</h1>
    <h3>{{ sub_banner }}</h3>
    <p>{{ time }}</p>
  </div>
</template>

<script>
import moment from "moment";
export default {
  props: ["banner", "sub_banner"],
  name: "HelloWorld",
  data() {
    return {
      time: moment().format("YYYY")
    };
  }
};
</script>
