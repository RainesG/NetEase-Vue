<template>
  <div id="app">
    <topbar/>
  </div>
</template>

<script>
import topbar from "./components/topbar.vue";

export default {
  name: "App",
  props:{
  },
  components: {
    topbar,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  margin-top: 0;
}
</style>
