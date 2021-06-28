<template>
  <div>
    <h2>兄弟组件</h2>
  </div>
</template>

<script>
export default {
  name: "Brother",
  created() {
    this.$bus.$on("sayLoveToBro", this.getlove);
  },
  methods: {
    getlove(e) {
      console.log("兄弟组件" + e);
    },
  },
};
</script>

<style>
</style>