<template>
  <div class="home">
    <img alt="CXX" src="../assets/logo.png" />
    <Father />
  </div>
</template>

<script>
import Father from "../components/Father.vue";
// @ is an alias to /src

export default {
  name: "Home",
  components: {
    Father,
  },
};
</script>
