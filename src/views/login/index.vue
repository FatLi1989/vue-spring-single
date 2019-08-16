<template>
  <div class="login-background">
    <div class="page-container">
      <div class="login-block">
        <a href="#" @click="toAccountLogin()">账号登录</a>
        <a href="#" @click="toMobileLogin()">免密登录</a>
      </div>
      <div>
        <form ref="account" v-show="isAccount">
          <input type="text" name="username" class="username" placeholder="用户名">
          <input type="password" name="password" class="password" placeholder="密码">
          <div class="account">
            <input type="text" name="imageCode" placeholder="验证码">
            <img :src="image">
          </div>
          <button type="submit">登录</button>
          <div class="error"><span>+</span></div>
        </form>

        <form ref="mobile" v-show="isMobile">
          <div class="mobile">
            <input type="text" class="mobile-fornt" name="mobile" placeholder="+86" disabled="disabled">
            <input type="password" class="mobile-context password" name="password" placeholder="手机号">
          </div>
          <div class="mobile-validate">
            <input type="text" name="imageCode" placeholder="验证码">
            <button type="button" onclick="sendSms()">获取验证码</button>
          </div>
          <button @click="login()">登录</button>
          <div class="error"><span>+</span></div>
        </form>
        <div>
          <div class="connect">
            <p>Or connect with:</p>
            <p>
              <a class="facebook" href=""></a>
              <a class="twitter" href=""></a>
            </p>
          </div>
        </div>
        <div align="center">Collect from <a href="http://www.google.com/" target="_blank" title="spring-security">spring-security</a>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { signIn } from '../../api/user'
export default {
  name: 'Login',
  data() {
    return {
      image: '',
      isMobile: false,
      isAccount: true
    }
  },
  created() {
    signIn.getImage()


  },
  methods: {
    toAccountLogin: function() {
      this.isAccount = true
      this.isMobile = false
    },
    toMobileLogin: function() {
      this.isAccount = false
      this.isMobile = true
    },
    login: function() {
    }
  }
}
</script>
<style scoped src="../../styles/reset.css"></style>
<style scoped src="../../styles/supersized.css"></style>
<style scoped src="../../styles/style.css"></style>
<style scoped src="../../styles/google.css"></style>
