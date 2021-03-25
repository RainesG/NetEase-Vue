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
          ><a href="#"
            ><em>下载客户端</em></a
          ></span
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
      <button class="create mr10"><a href="">创作者中心</a></button>
      <button class="login">
        <a href="#" @click="qr_login()">登录</a>
      </button>
    </div>
    <login class="login-part" :changeStatus='isShow' v-show="isShow"/>
  </div>
</template>


<script>
import axios from "axios";
import login from "./login";
export default {
  name: "topbar",
  components: {
    login,
  },
  data() {
    return {
      isShow : false
    }
  },
  methods: {

    qr_login() {
      this.isShow = !(this.isShow)
      // console.log("succes");
      // var that = this;
      //   console.log(this.isShow);
      //   that.isShow = true
      axios.defaults.baseURL = "https://music.hzbiz.net/";
      var url = "login/qr/key?e=" + new Date();
      var params = {};

      // console.log('asd'+info);
      axios
        .post(url, params)
        .then((res) => {
          // console.log(res.data.data.unikey);

          // Create Qr Code
          var url = "login/qr/create?e=" + new Date();
          var params = {
            key: res.data.data.unikey,
            qrimg: 1,
          };

          axios
            .post(url, params)
            .then((res) => {
              // console.log(res.data.data.qrimg);
              var qr = document.getElementsByClassName("qrImg")[0];
              qr.src = res.data.data.qrimg;
            })
            .catch((err) => {
              console.error(err);
            });

          // check QrScanning status
          function checkStatus(res) {
            var url = "login/qr/check?e=" + new Date();
            var params = {
              key: res.data.data.unikey,
            };

            axios
              .post(url, params)
              .then((res) => {
                // console.log(res.data.code);
                if (res.data.code == "803") {
                  clearInterval(timeId);

console.log(res);
                  console.log("success");
                  var url = "login/refresh";
                  var params = {};
                  axios
                    .post(url, params)
                    .then((res) => {
                      console.log(res);
                    })
                    .catch((err) => {
                      console.error(err);
                    });
                }
              })
              .catch((err) => {
                console.error(err);
              });
          }

          const timeId = setInterval(() => {
            checkStatus(res);
            // console.log('turn');
          }, 1000);
        })
        .catch((err) => {
          console.error(err);
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
.mr10 {
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

a {
  color: #ccc;
  text-decoration: none;
}

a:hover {
  color: #fff;
}

.list {
  height: 70px;
  margin: 0;
}

.list li:hover {
  background-color: #000;
}

.list li {
  display: inline-block;
  padding: 0 20px;
  line-height: 70px;
  margin: 0;
  position: relative;
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
  padding: 0;
  height: 70px;
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

.list li sup {
  display: block;
  width: 28px;
  height: 19px;
  position: absolute;
  top: 21px;
  left: 100px;
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

.srchbg input::focus {
  color: rebeccapurple;
}

.create {
  width: 90px;
  height: 32px;
  box-sizing: border-box;
  border: 1px solid #4f4f4f;
  background-position: 0 -140px;
  line-height: 32px;
  background-color: transparent;
  border-radius: 20px;
}

.create:hover {
  text-decoration: none;
  border: 1px solid #ccc;
  color: #fff;
}

.login {
  border: none;
  background-color: transparent;
  outline: none;
}

.login a {
  text-decoration: #333;
}

.topbar {
  position: relative;
}

.login-part {
  position: absolute;
  top: 100px;
  margin: 0;
}
</style>
