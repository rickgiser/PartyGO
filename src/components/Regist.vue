<template>
  <div class="regist">
      <div class="regist-input">
          <div class="regist-passworld">
              <form action="">
                  <div class="input-name">
                      <div class="input-img"></div>
                      <input class="username" id="username" type="text" placeholder="请输入手机号/邮箱/用户名" v-model="userName"></input>
                  </div>
                  <div class="input-passworld">
                      <div class="input-img"></div>
                      <input class="passworld" type="text" placeholder="请输入密码" v-model="passWorld" id="pas1">
                  </div>
                  <div class="input-passworld">
                      <div class="input-img"></div>
                      <input class="passworld" type="text" placeholder="确认密码" v-model="passWorldAgain" id="pas2">
                      <span class="codea appear">两次输入的密码不一致！</span>
                  </div>
              </form>
          </div>
      </div>
      <div class="vali">
          <input type="text" placeholder="验证码" class="vali-input" v-model="codeNum" v-on:blur="checkLpicma">
          <input type="button" id="code" @click="createCode"  class="verification1" v-model="checkCode" />
          <span class="notice disappear" >请输入正确的验证码</span>
      </div>
      <div class="regist-bottom">
          <mt-button type="primary" class="registf" v-on:click="handleRegist">注册</mt-button>
      </div>
      <div class="closelogin" @click="closelogin"><img src="../assets/login/close.png"></div>
  </div>
</template>
<script>
export default {
  name:"regist",
  data(){
      return {
          checkCode:'',
          userName:'',
          passWorld:'',
          passWorldAgain:'',
          codeNum:''
      }
  },
  methods:{
      // 图片验证码生成
      createCode (){
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
      },
      /* 检验验证码 */
      checkLpicma (){
          this.codeNum.toUpperCase();//取得输入的验证码并转化为大写         
          if(this.codeNum == '') {
              $(".vali span:eq(0)").text("请输入验证码");
              $(".vali span:eq(0)").removeClass("disappear");
             
          }else if(this.codeNum.toUpperCase() != this.checkCode ) { //若输入的验证码与产生的验证码不一致时    
                      
              $(".vali span:eq(0)").text("请输入正确的验证码！")
              $(".vali span:eq(0)").removeClass("disappear");
              this.createCode();//刷新验证码   
              this.codeNum = '';
          }else { 
              //输入正确时   
              $(".vali span:eq(0)").addClass("disappear");
              return true;
          } 
      },
      handleRegist (){
          //  判断两次输入的密码是否一致
          if($("#pas1").val() != $("#pas2").val()){
              $(".input-passworld span:eq(0)").removeClass("appear");
          }else{
              $(".input-passworld span:eq(0)").addClass("appear");
          }
          // ajax  方式实现注册功能
          
          /* if(!isUsernameValid || !isPwdValid){ //用if语句来判断当用户名或者密码有一个为false时就弹出一个消息框，并提示：请输入正确的信息。
          alert('请输入正确的信息');
          return;  //结束
            } */
            $.ajax({       
            type:"post", 
            url:Config.serviceURL+"/user", 
            data:{
                username:$("#username").val(),  
                password:$("#pas1").val() 
            },
            success:function(data){
                console.log(data);
                alert("注册成功");
                // window.location = "login.html"; 
            },
            error:function(error){
                console.log(error);
            }
        });
      }
  },
  mounted(){
      this.createCode();
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
                    .codea{
                        font-size:12px;
                        color:red;
                        margin-left:80px;
                    }
                    .appear{
                        visibility: hidden;
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
                margin-top: 4px;
                margin-left:8px;
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
                margin-top:3px;
            }
            .notice{
                font-size:12px;
                margin-left:-9px;
                color:red;
            }
            .disappear{
                visibility:hidden;
            }
        }
        .registf{
            position: absolute;
            height: 40px;
            width: 90%;
            margin-top:80px;
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



