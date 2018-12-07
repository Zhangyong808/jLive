<template xmlns="http://www.w3.org/1999/html">
    <div>
      <!--巨立logo+登录-->
      <div class="ld">
        <div>
          <img src="../../static/image/0C5C87A3-1922-4323-9C6F-1DC17A396EFA@2x.png" alt="">
        </div>
        <input type="text" placeholder="请输入用户名" class="userName"><br>
        <input type="text" placeholder="请输入密码" class="password"><br>
        <button class="dbind" @click="dbind">绑定</button>
      </div>
    </div>
</template>

<script>
    export default {
        name: "joylive",
        data(){
          return{
            arr:[]
          }
        },
        methods:{
          dbind(){
            var userName=$('.userName').val();
            var password=$('.password').val();
            var params = new URLSearchParams();
            //params.append('openId',this.openId);
            params.append('userName',userName);
            params.append('password',password);
            axios.post('http://wx.baronli.com/api/user/openIdAndUser/'+this.openId+'/'+userName+'/'+password,params).then(function(res){
              //判断密码是否正确
              if(res.data.success == true){
                console.log(res.data);
                //正确
                //console.log(res.data['data']['userInfo']['personId']);
                localStorage.setItem('personId',res.data['data']['userInfo']['personId']);
                localStorage.setItem('personName',res.data['data']['userInfo']['name']);
                this.$router.push('/maincontent');
              }else{
                //错误
                alert('请检查账号密码是否正确')
              }
            }.bind(this));
          }
        },
        mounted(){
          //从后台返回的路径获取openId以及userId
          this.openId = this.$route.query.openId;
          // this.personId = this.$route.query.personId;
          if(this.personId !=''){
            localStorage.setItem('personId',this.personId);
            //测试拿一个固定的值
            localStorage.setItem('personId','402880826408a9800164092a68e5016c');
            this.$router.push('/maincontent');
          }
        }
    }
</script>

<style scoped>
  .ld{text-align: center;margin-top: 17.6rem;}
  .ld>div{margin-bottom: 8.2rem;}
  .ld>div>img{width: 35.4rem;height: 20.6rem;}
  .ld>input{width: 47.8rem;height: 6rem;border-bottom:2px solid #979797;text-align: center;font-size:3.2rem;margin-bottom: 6.7rem;padding-bottom: 2rem;}
  .ld>input::placeholder{font-size:3.2rem;color:#9b9b9b;}
  .dbind{width: 47.8rem;height: 8rem;background: #ef2905;font-size:3.6rem;color:#ffffff;border-radius: 10px;margin-top:6.8rem;line-height: 8rem;}
</style>
