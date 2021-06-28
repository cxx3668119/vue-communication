<template>
  <div>
    <h3>孙子组件</h3>
    <h5>爷爷给的值=====>{{ count }}</h5>
  </div>
</template>

<script>
export default {
  name: "GrandSon",
  inject: ["father"],
  data() {
    return {
      count: this.father.count,
    };
  },
};
</script>

<style>
</style>