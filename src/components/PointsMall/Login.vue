<template>
    <div class="divlogin">
      <span class="login">登录</span>
      <img class="sanjiao" src="../../../static/image/sanjiao@2x.png" alt="">
      <div>
        <img class="peo" src="../../../static/image/people.png" alt="">
        <input class="zh" type="text" placeholder="请输入账号">
        <br>
        <img class="jia" src="../../../static/image/jiami.png" alt="">
        <img id="demo_img" @click="hideShowPsw()" src="../../../static/image/hidden.png" alt="">
        <input id="demo_input" type="password" placeholder="请输入密码">
        <p @click="enter">登录</p>
      </div>
    </div>
</template>

<script>
    export default {
        name: "login",
        methods:{
          hideShowPsw(){
           var demoImg = document.getElementById("demo_img");
           var demoInput = document.getElementById("demo_input");
           //隐藏text block，显示password block
           if (demoInput.type == "password") {
           demoInput.type = "text";
           demo_img.src = "../../../static/image/display.png";
           }else {
           demoInput.type = "password";
           demo_img.src = "../../../static/image/hidden.png";
            }
           },
           enter(){
             if(($('#demo_input').val()=='')||($('.zh').val()=='')){
               alert('请正确输入账号或者密码');
             }else{
             }
           }
        }
    }
</script>

<style scoped>
  .divlogin{position: relative;text-align: center;}
  .login{font-family: PingFang-SC-Regular;font-size: 13.2rem;font-weight: normal;font-stretch:normal;color: #888888;opacity: 0.38;position:absolute;top:18.6rem;right:5.9rem;}
  .sanjiao{width: 39.7rem;position:absolute;top: 16.2rem;left:0;}
  .divlogin>div{position: absolute;top: 52.1rem;left: 10%;width: 80%;}
  .divlogin>div>input{width: 75%;height: 9.8rem;background-color: whitesmoke;border-radius: 49px;padding-left: 13.6rem;margin-bottom: 4.4rem;font-size: 3.4rem;}
  .divlogin>div>input::placeholder{font-family: PingFang-SC-Light;font-size: 3.4rem;font-weight: normal;font-stretch: normal;color: #b2b2b2;}
  .divlogin>div>p{height: 9.8rem;background-color: whitesmoke;border-radius: 49px;line-height: 9.8rem;font-family: PingFang-SC-Bold;font-size: 3.6rem;font-weight: normal;font-stretch: normal;color: #fd7b88;margin-top: 14.2rem;}
  .divlogin>div>img{width: 3.5rem;height: 4rem;}
  .peo{position:absolute;top: 2.9rem;left: 6.8rem;}
  .jia{position:absolute;top: 17.5rem;left: 6.8rem;}
  #demo_img{width: 3.9rem;height: 2.1rem;position:absolute;top:18.5rem;right: 4.1rem;}
</style>
