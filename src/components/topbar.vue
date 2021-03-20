<template>
  <div class="topbar">
    <h1 class="logo">
      <a href="#">网易云音乐</a>
    </h1>
    <ul class="list">
      <li>
        <span
          ><a href="#"><em>发现音乐</em></a></span
        >
      </li>
      <li>
        <span
          ><a href="#"><em>我的音乐</em></a></span
        >
      </li>
      <li>
        <span
          ><a href="#"><em>朋友</em></a></span
        >
      </li>
      <li>
        <span
          ><a href="#"><em>商城</em></a></span
        >
      </li>
      <li>
        <span
          ><a href="#"><em>音乐人</em></a></span
        >
      </li>
      <li>
        <span
          ><a href="#"><em>下载客户端</em></a></span
        >
        <sup class="hot"></sup>
      </li>
    </ul>

    <div class="r-topbar">
      <div class="srchbg mr10">
        <input
          type="text"
          name="srch"
          id="srch"
          class="txt j-flag"
          value=""
          style="opacity: 1"
          placeholder="音乐/视频/电台/用户"
        />
      </div>
      <button class="create mr10">创作者中心</button>
      <button class="login"><a href="#">登录</a></button>
    </div>
  </div>
</template>

<script>
export default {
  name: "topbar",
  props: {
    msg: String,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.mr10{
  margin-right: 10px;
}
em {
  font-style: normal;
  font-size: 14px;
}

ul {
  list-style-type: none;
  padding: 0;
  height: 100%;
}

li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #fff;
  text-decoration: none;
}

.list {
  display: flex;
  justify-content: space-evenly;
}

.topbar {
  max-width: 1200px;
  margin: 0 auto;
  display: flex;
  justify-content: space-evenly;
  /* position: relative; */
  /* z-index: 1000; */
  /* height: 70px; */
  box-sizing: border-box;
  background: #242424;
  border-bottom: 1px solid #000;
  align-items: center;
}

.r-topbar {
  display: flex;
  align-items: center;
}

.logo a {
  box-sizing: border-box;
  background: url(../assets/topbar.png) no-repeat 0 -20px;
  color: transparent;
}

.list li {
  position: relative;
  height: 100%;
}

.list li sup {
  display: block;
  width: 28px;
  height: 19px;
  position: absolute;
  top: -5px;
  left: 75px;
  background: url(../assets/topbar.png) no-repeat -190px 0;
}

.srchbg input {
  background: url(../assets/topbar.png) no-repeat 0 -99px;
  background-color: #fff;
  border-radius: 32px;
  width: 158px;
  height: 32px;
  line-height: 32px;
  position: relative;
  text-indent: 1.5rem;
  outline: none;
}

.create {
  width: 90px;
  height: 32px;
  box-sizing: border-box;
  border: 1px solid #4f4f4f;
  background-position: 0 -140px;
  line-height: 32px;
  color: #ccc;
  background-color: transparent;
  border-radius: 20px;
}

.login{
  border: none;
  background-color: transparent;
}

.login a{
  text-decoration: #333;
}
</style>
