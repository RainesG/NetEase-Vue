<template>
  <div id="app">
    <topbar msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
import topbar from './components/topbar.vue'

export default {
  name: 'App',
  components: {
    topbar
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  background-color: #242424;
  margin-top: 0;
}
</style>
