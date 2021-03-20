<template>
  <div class="m-layer" v-show="true">
    <div class="title-bar">
      <div class="title">登录</div>
      <div class="close"></div>
    </div>

    <div class="login-content">
      <div class="login-list hide">
        <div class="left">
          <div class="u-wrap">
            <div class="u-main"></div>
          </div>
          <button class="phone-login">手机号登录</button>
          <button class="regist">注册</button>
        </div>

        <div class="right">
          <div class="u-alt">
            <ul>
              <li>
                <a>微信登录</a>
              </li>
              <li>
                <a>QQ登录</a>
              </li>
              <li>
                <a>微博登录</a>
              </li>
              <li>
                <a>网易邮箱帐号登录</a>
              </li>
            </ul>
          </div>
        </div>
      </div>

      <div class="login-scan">
        <div class="main">
          <div class="phone"></div>
          <div class="qr"></div>
        </div>
        <div class="switch" @click="login_switch()">
          <button>选择其他登录模式</button>
        </div>
      </div>
    </div>
  </div>
</template>


<script>
export default {
  name: "login",
  props: {
    isShow: {},
  },
  methods: {
    login_switch() {
      console.log(document.getElementsByClassName("login-scan")[0].classList);
      document.getElementsByClassName("login-scan")[0].classList += " hide";
      document.getElementsByClassName("login-list")[0].classList.remove("hide");
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
ul,li{
  list-style: none;
}

.hide {
  display: none;
}

.mr10 {
  margin-right: 10px;
}

em {
  font-style: normal;
  font-size: 14px;
}

.m-layer {
  width: 530px;
  border-radius: 4px;
  box-shadow: 0 5px 16px rgb(0 0 0 / 80%);
  border: none;
  margin: 20px auto;
}

.title {
  border-radius: 3px 3px 0 0;
  font-weight: bold;
  font-size: 14px;
  color: #fff;
  text-align: start;
  float: left;
}

.close {
  /* position: absolute; */
  float: right;
  /* color: white; */
  width: 20px;
  height: 20px;
  background: url(../assets/layer.png) no-repeat 0 -90px;
}

.title-bar {
  border-bottom: 1px solid #191919;
  border-radius: 4px 4px 0 0;
  background: #2d2d2d;
  /* background: url(../assets/layer.png) no-repeat 0 -60px; */
  background-size: cover;
  padding: 10px 20px;
}

.title-bar::after {
  content: "";
  display: block;
  clear: both;
}

.login-content {
  padding: 38px 0 20px;
  box-sizing: border-box;
  border: 1px solid #878787;
  border-width: 0 1px 1px;
  border-radius: 0 0 4px 4px;
  background: #fff;
  min-height: 274px;
}

.phone {
  background: url(../assets/qr_guide.png) no-repeat;
  background-size: contain;
  margin-left: 101px;
  width: 125px;
  height: 220px;
  margin-right: 20px;
}

.switch button {
  cursor: pointer;
  width: 118px;
  height: 100%;
  margin: 20px auto 0;
  font-size: 12px;
  border: 1px solid #979797;
  border-radius: 15px;
  line-height: 28px;
  text-align: center;
  color: rgba(0, 0, 0, 0.8);
  background-color: transparent;
  outline: none;
}

.main {
  display: flex;
}

.main::after {
  content: "";
  display: block;
  clear: both;
}

.u-main {
  background: url("../assets/platform.png") no-repeat 13px 0;
  height: 120px;
}

.u-wrap {
  float: left;
  width: 224px;
  padding: 0 35px 3px 40px;
  border-right: 1px dotted #ccc;
}

.login-list button {
  display: block;
  width: 219px;
  height: 31px;
  line-height: 31px;
  color: #fff;
  border: none;
  outline: none;
  background: url(../assets/button2.png);
  background-position: right -385px;
  margin: 0 auto;
}

.login-list {
  display: flex;
}

.login-list.left {
  display: flex;
  flex-direction: column;
}
</style>
