<template>
  <div class="footer fixed">
    <p class="text-muted small mb-0">{{ banner }}</p>
    <p class="text-muted small mb-0">{{ link }}</p>
  </div>
</template>

<script>
export default {
  name: "Footer",
  props: ["banner", "link"],
  data() {
    return {};
  },
  methods:{
    transfer() {
      this.$emit("transfer", "test");
    }
  },
  mounted(){
    this.transfer();
  }
};
</script>

<style scoped>

</style>
