<template>
  <div class="footer fixed">
    <p class="text-muted small mb-0">{{ banner }}</p>
    <p class="text-muted small mb-0">
      <a :href="link">{{ link }}</a>
    </p>
  </div>
</template>

<script>
export default {
  name: "Footer",
  props: ["banner", "link"],
  data() {
    return {};
  },
  methods: {},
};
</script>

<style scoped>

</style>
