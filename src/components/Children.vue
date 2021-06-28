<template>
  <div class="children">
    <h2>子组件</h2>
    <div>
      父亲组件传过来的值=====>
      <span style="color: pink">{{ count }}</span>
    </div>
    <grand-son></grand-son>
    <button @click="sayLove">表达爱意</button>
  </div>
</template>

<script>
import GrandSon from "./GrandSon.vue";
export default {
  props: ["count"],
  components: {
    GrandSon,
  },
  mounted() {
    console.log(this.$parent.count + " =====> parent");
  },
  data() {
    return {
      cxx: "star",
    };
  },
  methods: {
    sayLove() {
      this.$emit("sayLove", "I love you cxx");
      this.$bus.$emit("sayLoveToBro", "I love you cxxBro");
    },
  },
};
</script>

<style>
</style>