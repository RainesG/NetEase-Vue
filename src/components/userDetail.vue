<template>
  <div class="m-layer">
    <main>
      <img class="avatar" />
      <div class="main">
        <ul class="albumList"></ul>
        <ul class="songList"></ul>
      </div>
      <div class="playerContainer"><audio controls></audio></div>
    </main>
  </div>
</template>

<script>
export default {
  name: "userDetail",
  props: {},
  methods: {},
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
a {
  text-decoration: none;
}

ul,
li {
  list-style: none;
}

.main{
  display: flex;
  justify-content: stretch;
}

.avatar {
  width: 100px;
  height: 100px;
}

.albumList {
  color: white;
  background-color: #252525;
  border-radius: 0.5rem;
}

main {
  width: 1200px;
  margin: 0 auto;
  margin-top: 10px;
  display: flex;
  justify-content: space-between;
  padding: 20px 100px;
}
</style>
