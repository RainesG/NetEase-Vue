<template>
  <div class="m-layer" v-show="isShow">
    <div class="title-bar">
      <div class="title">登录</div>
      <div class="close" @click="hideThis()"></div>
    </div>

    <div class="login-content">
      <div class="login-list hide">
        <div class="left">
          <div class="u-wrap">
            <div class="u-main"></div>
          </div>
          <div class="btn">
            <button class="phone-login" @click="phone_show()">
              手机号登录
            </button>
            <button class="regist">注册</button>
          </div>
          <div class="u-official-terms">
            <input type="checkbox" placeholder="同意" />
            <a href="#" target="_blank" style="color: #507daf">《服务条款》</a>
            <a href="#" target="_blank" style="color: #507daf">《隐私政策》</a>
            <a href="#" target="_blank" style="color: #507daf"
              >《儿童隐私政策》</a
            >
          </div>
          <div class="n-scan" @click="login_switch()"></div>
        </div>

        <div class="right">
          <div class="u-alt">
            <ul>
              <li>
                <span class="wechat"></span>
                <a>微信登录</a>
              </li>
              <li>
                <span class="qq"></span>
                <a>QQ登录</a>
              </li>
              <li>
                <span class="weibo"></span>
                <a>微博登录</a>
              </li>
              <li>
                <span class="netease"></span>
                <a>网易邮箱帐号登录</a>
              </li>
            </ul>
          </div>
        </div>
      </div>

      <div class="login-scan">
        <div class="main">
          <div class="phone"></div>
          <div class="qr"><img src="" class="qrImg" /></div>
        </div>
        <div class="switch" @click="login_switch()">
          <button>选择其他登录模式</button>
        </div>
      </div>
    </div>

    <div class="login-phone hide">
      <form action="" id="login" @submit="phone_login()">
        <input
          type="text"
          placeholder="Phone Number"
          class="userInput"
          v-model="phone"
        />
        <input
          type="password"
          placeholder="Password"
          class="userInput"
          v-model="pw"
        />

        <div class="forget-pw">
          <label for="f-pw"
            ><input type="checkbox" name="f-pw" id="" />自动登录</label
          >
          <a href="#">忘记密码？</a>
        </div>

        <button @click="phone_login()">登录</button>
      </form>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "login",
  props: {
    isShow: { type: Boolean, default: false },
  },
  data() {
    return {
      phone:'',
      pw:''
    }
  },
  watch: {
    showMask() {
      this.$emit("changeStause", this.isShow);
    },
  },
  methods: {
    hideThis: function () {
      this.isShow = false;
      console.log(this.isShow);
    },

    login_switch() {
      // console.log(document.getElementsByClassName("login-scan")[0].classList);

      if (
        document
          .getElementsByClassName("login-scan")[0]
          .classList.toString()
          .includes("hide")
      ) {
        document
          .getElementsByClassName("login-scan")[0]
          .classList.remove("hide");
        document.getElementsByClassName("login-list")[0].classList += " hide";
        document
          .getElementsByClassName("login-list")[0]
          .classList.remove("flex");
      } else {
        document.getElementsByClassName("login-scan")[0].classList += " hide";
        document
          .getElementsByClassName("login-list")[0]
          .classList.remove("hide");
        document.getElementsByClassName("login-list")[0].classList += " flex";
      }
    },

    phone_show() {
      if (
        document
          .getElementsByClassName("login-content")[0]
          .classList.toString()
          .includes("hide")
      ) {
        document
          .getElementsByClassName("login-content")[0]
          .classList.remove("hide");
        document.getElementsByClassName("login-phone")[0].classList += " hide";
        document
          .getElementsByClassName("login-phone")[0]
          .classList.remove("flex");
      } else {
        document.getElementsByClassName("login-content")[0].classList +=
          " hide";
        document
          .getElementsByClassName("login-phone")[0]
          .classList.remove("hide");
        document.getElementsByClassName("login-phone")[0].classList += " flex";
      }
    },

    phone_login() {
      axios.defaults.baseURL = "https://music.hzbiz.net/";

      console.log(this);
      var phone = this.phone;
      var pw = this.pw;
      var url = "login/cellphone";
      var params = {
        phone: phone,
        password: pw,
      };

      axios
        .post(url, params)
        .then((res) => {
          console.log(res);
          axios.post(url, params).then((res) => {
            console.log(res);
            var avatar = document.createElement("img");
            var img = document.getElementsByTagName("main");
            img[0].append(avatar);
            avatar.src = res.data.profile.avatarUrl;
            console.log(res.data.profile.userId);
          });
        })
        .catch((err) => {
          console.error(err);
        });
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.flex {
  display: flex;
}

a {
  text-decoration: none;
}

ul,
li {
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

.login-scan {
  padding: 38px 0 20px;
}

.login-content {
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
  width: 220px;
  height: 31px;
  line-height: 31px;
  border: none;
  outline: none;
  margin: 5px auto;
  border-radius: 0.3rem;
}

.phone-login {
  background: url(../assets/button2.png);
  background-position: right -385px;
  color: #fff;
}

.regist {
  background: url(../assets/button2.png);
  background-position: right -59px;
  color: #333;
}

.login-list .left {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.login-list {
  padding: 48px 0;
}

.u-official-terms {
  margin-top: 15px;
  font-family: NotoSansHans-Regular;
  font-size: 10px;
  color: rgba(0, 0, 0, 0.4);
  line-height: 15px;
}

.n-scan {
  position: absolute;
  width: 52px;
  height: 52px;
  right: 1px;
  bottom: 1px;
  background: url(../assets/qr_login_icon.png) no-repeat;
  background-size: contain;
  cursor: pointer;
}

.u-alt span {
  display: block;
  width: 38px;
  height: 38px;
}

.u-alt li {
  display: flex;
  font-size: 12px;
  color: #333;
  line-height: 38px;
  text-indent: 20px;
  margin-top: 10px;
}

.wechat {
  background: url(../assets/logo.png) no-repeat;
  background-position: -150px -670px;
}

.qq {
  background: url(../assets/logo.png) no-repeat;
  background-position: -190px -670px;
}

.weibo {
  background: url(../assets/logo.png) no-repeat;
  background-position: -231px -670px;
}

.netease {
  background: url(../assets/logo.png) no-repeat;
  background-position: -271px -670px;
}

.userInput {
  display: block;
  width: 200px;
  height: 20px;
  margin: 0 auto;
  margin-top: 10px;
  outline: none;
}

form {
  width: 100%;
  height: 200px;
}

.forget-pw {
  width: 200px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin: 0 auto;
  font-size: 12px;
  margin-top: 10px;
}

.login-phone {
  padding: 30px 0 43px;
  widows: 220px;
  margin: 0 auto;
}

.login-phone button {
  display: block;
  margin: 0 auto;
  margin-top: 20px;
  width: 200px;
  height: 31px;
  background: url(../assets/button2.png);
  background-position: right -550px;
  outline: none;
  border: none;
  border-radius: 0.3rem;
  color: white;
}
</style>
