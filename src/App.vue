<template>
  <div id="app">
    <topbar msg="Welcome to Your Vue.js App" />
    <login/>
  </div>
</template>

<script>
import topbar from "./components/topbar.vue";
import login from "./components/login.vue";

export default {
  name: "App",
  props:{
  },
  components: {
    topbar,
    login,
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
