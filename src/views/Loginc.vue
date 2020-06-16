<template>
  <div class="loginc">
    <div><img src="@/assets/logo.png" alt=""></div>
    <div class="lp">
      <!-- 号码输入框 -->
    <inputc type="tel" placeholder="手机号" btnt="获取验证码" error="号码错误" @btnclick="btnclick"/>
     <!-- 验证码输入框 -->
    <inputc type="text" placeholder="验证码"  error="验证码错误" />
     <!-- 登陆框 -->
   
    </div>
    <!-- 登陆按钮 -->
    <div><button @click="login">登陆</button></div> 
    

  </div>
</template>

<script>
import inputc from '@/components/inputc.vue';
export default {

  components: {
    inputc
  }
,
  methods:{
    // 输入框
    input(){

    },
    // 验证码
    btnclick(){
      let time=60
      let timer=setInterval(()=>{
        if (time==0){
          clearInterval(timer)
          this.btnt="获取验证码"
          this.disabled= false
        }
        else{
          this.btnt=time+"秒重试"
          this.disabled=true
          time--
        }
      },1000)
      console.log(time);
      

    },
    // 登陆
    login(){

    }
  }
}
</script>

<style lang="less" scoped>

.loginc{
  display :flex;
  flex-direction: column;
  align-items: center;
  
  button{
    width: 300px;
    height: 30px;
    background-color: yellowgreen;
    border: 1px solid steelblue;
    font-size: 16px;
  }
}

</style>
