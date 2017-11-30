<template>
  <div class="regist">
      <div class="regist-input">
          <div class="regist-passworld">
              <form action="">
                  <div class="input-name">
                      <div class="input-img"></div>
                      <input class="username" type="text" placeholder="请输入手机号/邮箱/用户名"></input>
                  </div>
                  <div class="input-passworld">
                      <div class="input-img"></div>
                      <input class="passworld" type="text" placeholder="请输入密码">
                  </div>
                  <div class="input-passworld">
                      <div class="input-img"></div>
                      <input class="passworld" type="text" placeholder="确认密码">
                  </div>
              </form>
          </div>
      </div>
      <div class="vali">
          <input type="text" placeholder="验证码" class="vali-input">
          <input type="button" id="code" @click="createCode"  class="verification1" v-model="checkCode"/>
      </div>
      <div class="regist-bottom">
          <mt-button type="primary" class="registf">注册</mt-button>
      </div>
      <div class="closelogin" @click="closelogin"><img src="../assets/login/close.png"></div>
  </div>
</template>
<script>
export default {
  name:"regist",
  data(){
      return {
          checkCode:''
      }
  },
  methods:{
      // 图片验证码
      createCode(){
          var code = "";    
          var codeLength = 4;//验证码的长度   
          var random = new Array(0,1,2,3,4,5,6,7,8,9,'A','B','C','D','E','F','G','H','I','J','K','L','M','N','O','P','Q','R',   
           'S','T','U','V','W','X','Y','Z');//随机数   
          for(var i = 0; i < codeLength; i++) {//循环操作   
              var index = Math.floor(Math.random()*36);//取得随机数的索引（0~35）   
              code += random[index];//根据索引取得随机数加到code上   
          }   
              this.checkCode = code;//把code值赋给验证码   
      },
      closelogin (){
        $(".regist").css({"display":"none"})
      }
  }
}
</script>

<style lang="less">
    .regist{
        position: relative;
        width: 80%;
        height: 50%;
        top: 25%;
        position: absolute;
        left: 10%;
        font-size: 15px;
        color: #90a4ae;
        background-color: white;
        .regist-input{
            height:47%;
            width:100%;
            // border:1px solid red;
            margin-top:30px;
            .regist-passworld{
                .input-name{
                    height: 40px;
                    .input-img{
                        position: absolute;
                        margin-left:14px;
                        margin-top:10px;
                        float: left;
                        width:20px;
                        height:20px;
                        background-image: url(http://a.amap.com/lbs-p/static/img/sprite-7676224642.png);
                        background-position: -0px -142px; 
                    }
                    .username{
                        margin-left:15px;
                        width: 230px;
                        padding-left:30px;
                        height:40px;
                        outline: none;
                        border:none;
                        border-bottom:1px solid #cacbcc;
                    }
                } 
                .input-passworld{
                    margin-top:10px;
                    height:40px;
                    .input-img{
                        position: absolute;
                        margin-left:14px;
                        margin-top:10px;
                        float: left;
                        width:20px;
                        height:22px;
                        background-image: url(http://a.amap.com/lbs-p/static/img/sprite-7676224642.png);
                        background-position: -0px -162px; 
                    }
                    .passworld{
                        margin-left:15px;
                        width: 230px;
                        padding-left:30px;
                        height:40px;
                        border:0px;
                        outline: none;
                        border-bottom:1px solid #cacbcc;
                    }
                }
            }
        }
        .vali{
            position: absolute;
            margin-left:15px;
            width: 90%;
            height:40px;
            margin-top:15px;
            .vali-input{
                float: left;
                height: 35px;
                width:100px;
                text-align: center;
                outline: none;
                margin-top: 2px;
                margin-left:6px;
                font-size:16px;
            }
            .verification1{
                font-size:18px;
                // font-style:italic;
                float: left;
                height: 41px;
                width:130px;
                outline: none;
                margin-left:15px;
                margin-top:2px;
            }
        }
        .registf{
            position: absolute;
            height: 40px;
            width: 90%;
            margin-top:75px;
            margin-left:15px;
            
        }
        .closelogin{
            top:25px;
            right:10px;
            position: absolute;
            img{
                width:14px;
                height:14px;
            }
        }
    }
</style>



