<template>
  <div class="login">
      <div class="login-top">
          <span class="passworldLogin">密码登陆</span>
          <span class="split"></span>
          <span class="messageLogin">短信登陆</span>
      </div>
      <div class="login-input">
          <div class="login-passworld">
              <form action="">
                  <div class="input-name">
                      <div class="input-img"></div>
                      <input class="username" type="text" placeholder="请输入手机号/邮箱/用户名">
                  </div>
                  <div class="input-passworld">
                      <div class="input-img"></div>
                      <input class="passworld" type="text" placeholder="请输入密码">
                  </div>
              </form>
          </div>
          <div class="login-message">
                <div class="input-tel">
                      <div class="input-img"></div>
                      <input class="tel" type="text" placeholder="请输入手机号">
                </div>
                <div class="input-passworld">
                      <div class="input-img"></div>
                      <input class="passworld" type="text" placeholder="请输入密码">
                      <button class="sendcode">发送验证码</button>
                </div>
          </div>
      </div>
      <div class="thirdArea">
          <span class="otherAccount">其它账号登陆</span>
          <a href="" class="taobao"></a>
          <a href="" class="alipay"></a>
          <a href="" class="sina"></a>
          <a href="" class="qq"></a>
          <button class="login-button">登陆</button>
      </div>
      <div class="login-footer">
          <div class="autologin">
              <div class="chickIcon"></div>
              <span>下次自动登录</span>
          </div>
          <div class="link">
              <a href="">忘记密码</a>
              <a href="">免费注册</a>
          </div>
      </div>
      <div class="closelogin"></div>
  </div>
</template>

<script>
export default {
  
}
</script>

<style lang="less">
    .login{
        width: 80%;
        height: 50%;
        border: 1px solid red;
        top: 25%;
        position: absolute;
        left: 10%;
        font-size: 15px;
        color: #90a4ae;
    }
</style>



