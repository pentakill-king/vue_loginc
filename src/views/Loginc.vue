<template>
  <div class="loginc">
    <div><img
        src="@/assets/logo.png"
        alt=""
      ></div>
    <div class="lp">
      <!-- 号码输入框 -->
      <inputc
        type="tel"
        v-model="phone"
        placeholder="手机号"
        :btnt="btnt"
        :disabled="disabled"
        :error="error.phone"
        @btnclick="btnclick"
      />
      <!-- 验证码输入框 -->
      <inputc
        type="text"
        v-model="code"
        placeholder="验证码"
        :error="error.code"
      />
      <!-- 登陆框 -->

    </div>
    <!-- 登陆按钮 -->
    <div><button
        class="radius5"
        :disabled="disabledl"
        @click="login"
      >{{logint}}</button></div>

  </div>
</template>

<script>
import inputc from "@/components/inputc.vue";
export default {
  data() {
    return {
      code: "",
      phone: "",
      btnt: "获取验证码",
      error: {},
      disabled: false,
      disabledl: false,
      logint: "登陆"
    };
  },

  components: {
    inputc
  },
  methods: {
    // 输入框
    input() {},
    // 手机号验证
    vphone() {
      if (!/^1[34578]\d{9}$/.test(this.phone)) {
        this.$set(this.error, "phone", "号码错误");
        return false;
      } else {
        this.error={}
        return true;
      }
    },
    // 验证码6位数字
    changecode() {
      if (!/^\d{6}$/.test(this.code)) {
        this.$set(this.error, "code", "验证码错误");
        return false;
      } else {
        this.error={}
        return true;
      }
    },

    btnclick() {
      if (this.vphone()) {
        // 发送验证码请求

        // 验证码倒计时

        let time = 59;
        let timer = setInterval(() => {
          if (time == 0) {
            clearInterval(timer);

            this.btnt = "获取验证码";
            this.disabled = false;
          } else {
            this.btnt = time + "秒重试";
            this.disabled = true;
            time--;
          }
        }, 1000);
      }
    },
    // 登陆
    login() {
      if (this.changecode()) {
        // 发送登陆请求
        console.log(this.phone + "+" + this.code);
        // 登陆点击拦截3秒
        let time = 3;
        let timer = setInterval(() => {
          if (time == 0) {
            clearInterval(timer);
            this.logint = "登陆";
            this.disabledl = false;
          } else {
            this.logint = time + "秒重试";
            this.disabledl = true;
            time--;
          }
        }, 1000);
      }
    }
  }
};
</script>

<style lang="less" scoped>
.loginc {
  display: flex;
  flex-direction: column;
  align-items: center;

  button {
    width: 300px;
    height: 30px;
    background-color: yellowgreen;
    font-size: 16px;
    border: 1px solid yellowgreen;
    color: white ;
  }
}
</style>
