<template>
  <div id="app">
    <topbar />
    <userDetail/>
  </div>
</template>

<script>
import topbar from "./components/topbar.vue";
import userDetail from "./components/userDetail.vue"

export default {
  name: "App",
  props: {},
  components: {
    topbar,
    userDetail
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
  background-color: #242424;
  border-bottom: 1px solid #000;
}
</style>
