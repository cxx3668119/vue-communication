<template>
  <div class="father">
    <h1>父亲组件</h1>
    <children ref="son" :count="count" @sayLove="getLove" />
    <brother />
  </div>
</template>

<script>
import Children from "./Children.vue";
import Brother from "./Brother.vue";

export default {
  mounted() {
    console.log(this.$refs.son.cxx);
  },
  provide() {
    return {
      father: this, //给后代接收
    };
  },
  data() {
    return {
      count: 1,
    };
  },
  name: "Father",
  components: {
    Children,
    Brother,
  },
  methods: {
    getLove(e) {
      console.log(e);
    },
  },
};
</script>

<style>
</style>