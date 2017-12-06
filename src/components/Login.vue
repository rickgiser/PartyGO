<template>
  <div class="login">
      <div class="login-top">
          <span class="passworldLogin" v-on:click="pasLoad">密码登陆</span>
          <span class="split">|</span>
          <span class="messageLogin" v-on:click="mesLoad">短信登陆</span>
      </div>
      <div class="login-input">
          <div class="login-passworld">
              <form action="">
                  <div class="input-name">
                      <div class="input-img"></div>
                      <input class="username" type="text" placeholder="请输入手机号/邮箱/用户名"></input>
                  </div>
                  <div class="input-passworld">
                      <div class="input-img"></div>
                      <input class="passworld" type="text" placeholder="请输入密码">
                  </div>
              </form>
          </div>
          <div class="login-message" style="display:none;">
                <div class="input-tel">
                      <div class="input-img"></div>
                      <input class="tel" type="text" placeholder="请输入手机号">
                </div>
                <div class="input-passworld">
                      <div class="input-img"></div>
                      <input class="passworld" type="text" placeholder="请输入验证码">
                      <mt-button class="sendcode">发送验证码</mt-button>
                </div>
          </div>
      </div>
      <div class="thirdArea">
          <span class="otherAccount">其它账号登陆</span>
          <a href="" class="taobao"></a>
          <a href="" class="alipay"></a>
          <a href="" class="sina"></a>
          <a href="" class="qq"></a>
          <!-- <button class="login-button"></button> -->
          <mt-button class="login-button" type="primary" v-on:click="handleLogin">登陆</mt-button>
      </div>
      <div class="login-footer">
          <div class="autologin">
              <div class="chickIcon"></div>
              <span>下次自动登录</span>
          </div>
          <div class="link">
              <a href="">忘记密码</a>
              <a href=""><router-link to="./login/regist">免费注册</router-link></a>
          </div>
      </div>
      <div class="closelogin" @click="closelogin"><img src="../assets/login/close.png"></div>
  </div>
</template>
<script>
export default {
  name:"login",
  data(){
      return {

      }
  },
  methods:{
      mesLoad (){
        $(".login-passworld").css({"display":"none"});
        $(".login-message").css({"display":"block"});
        $(".passworldLogin").css({"color":"#90a4ae"});
        $(".messageLogin").css({"color":"#42a5f5"});
        $(".login-footer").css({"display":"none"});
      },
      pasLoad (){
        $(".login-passworld").css({"display":"block","color":"#90a4ae"});
        $(".login-message").css({"display":"none","color":"#42a5f5"});
        $(".passworldLogin").css({"color":"#42a5f5"});
        $(".messageLogin").css({"color":"#90a4ae"});
        $(".login-footer").css({"display":"block"});
      },
      closelogin (){
        $(".login").css({"display":"none"})
      }
  }
}
</script>

<style lang="less">
    .login{
        position: relative;
        width: 80%;
        height: 50%;
        top: 25%;
        position: absolute;
        left: 10%;
        font-size: 15px;
        color: #90a4ae;
        background-color: white;
        .login-top{
            height:30px;
            width:100%;
            margin-top:20px;
            padding-left:5px;
            line-height: 30px;
            .passworldLogin{
                color:#42a5f5;
            }
            span{
                margin-left:10px;
            }
        }
        .login-input{
            height:30%;
            width:100%;
            // border:1px solid red;
            margin-top:20px;
            .login-passworld{
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
            .login-message{
                .input-tel{
                    height: 40px;
                    .input-img{
                        position: absolute;
                        margin-left:14px;
                        margin-top:10px;
                        float: left;
                        width:20px;
                        height:24px;
                        background-image: url(http://a.amap.com/lbs-p/static/img/sprite-7676224642.png);
                        background-position: -0px -184px; 
                    }
                    .tel{
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
                    width:60%;
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
                        float: left;
                        margin-left:15px;
                        width: 125px;
                        padding-left:30px;
                        height:40px;
                        border:0px;
                        outline: none;
                        border-bottom:1px solid #cacbcc;
                    }
                    .sendcode{
                        color: #42a5f5;
                        border-radius: 0px;
                        font-size: 13px;
                        width:100px;
                        height:40px;
                        position: absolute;
                        float: left;
                        outline: none;
                        background-color: white;
                        margin-left:5px;
                        margin-top:2px;
                    }
                    
                }
            }
        }
        .thirdArea{
            margin-top:25px;
            height:65px;
            .otherAccount{
                display: block;
                margin-left:10px;
                margin-top:5px;
                margin-left:12px;
                font-size:10px;
            }
            .taobao{
                margin-top:10px;
                margin-left:12px;
                float: left;
                position: absolute;
                width:28px;
                height:28px;
                background-image: url(http://a.amap.com/lbs-p/static/img/sprite-7676224642.png);
                background-position: -0px -208px;
            }
            .alipay{
                margin-top:10px;
                margin-left:50px;
                float: left;
                position: absolute;
                width:28px;
                height:28px;
                background-position: -0px -264px;
                background-image: url(http://a.amap.com/lbs-p/static/img/sprite-7676224642.png);
            }
            .sina{
                margin-top:10px;
                margin-left:88px;
                float: left;
                position: absolute;
                width:28px;
                height:28px;
                background-position: -0px -404px;
                background-image: url(http://a.amap.com/lbs-p/static/img/sprite-7676224642.png);
            }
            .qq{
                margin-top:10px;
                margin-left:128px;
                float: left;
                position: absolute;
                width:28px;
                height:28px;
                background-position: -0px -348px;
                background-image: url(http://a.amap.com/lbs-p/static/img/sprite-7676224642.png);
            }
            .login-button{
                width:80px;
                height:30px;
                border-radius: 20px;
                // background-color: #42a5f5;
                margin-top: 5px;
                margin-left: 189px;
                outline: none;
                font-size: 16px;
            }
        }
        .login-footer{
            margin-top:20px;
            height:40px;
            .autologin{
                display: inline;
                margin-top:20px;
                width:100px;
                height:25px;
                .chickIcon{
                    margin-left:5px;
                    position: absolute;
                    float:left;
                    width:18px;
                    height:18px;
                    background-position: -0px -66px;
                    background-image: url(http://a.amap.com/lbs-p/static/img/sprite-7676224642.png);
                }
                span{
                    float: left;
                    font-size:14px;
                    position: absolute;
                    margin-left:27px;
                }
            }
            .link{
                position: absolute;
                float: left;
                width:150px;
                margin-left:140px;
                a{
                    color: #42a5f5;
                    font-size: 14px;
                    margin-left:8px;
                    text-decoration: none;
                }
            }
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



