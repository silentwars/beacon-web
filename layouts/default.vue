<style lang="less">
  @import "../assets/less/style_variable";

  .main-wrap {
    .beacon-header-wrap {
      background-color: #fff;
      height: 50px;
    }
    .header-content {
      width: 1200px;
      margin-left: auto;
      margin-right: auto;
      .index-logo {
        margin-top: 9px;
      }
      .new-article {
        display: inline-block;
        width: 88px;
        height: 34px;
        .bgImg("write_article.png");
        background-size: 100% 100%;
      }
      .reg-btn {
        .boder_radius(25px);
        padding: 6px 29px;
        margin-left: 51px;
        margin-right: 20px;
      }
      .index-link {
        color: @bluecolor;
        font-size: 16px;
        .iconfont {
          font-size: 18px;
          position: relative;
          top: 2px;
        }
      }
      .login-link {
        color: @graycolor;
        margin-left: 43px;
        .iconfont {
          font-size: 16px;
        }
      }
      .right-p {
        > a {
          display: inline-block;
          margin-top: -4px;
        }
        .new-article {
          position: relative;
          top: 11px;
        }
      }
      .login-info {
        margin: 0 35px;
        a {
          color: @graycolor;
        }
        .icon-sanjiaodown {
          color: @graycolor;
        }
      }
      .pic-img {
        width: 33px;
        position: relative;
        top: 10px;
      }

    }
    .main-content {
      width: 1000px;
      margin-top: 20px;
      margin-left: auto;
      margin-right: auto;
    }
  }
</style>
<template>
  <div class="main-wrap">
    <div class="beacon-header-wrap">
      <div class="header-content clearfloat">
        <img src="../assets/images/index_logo.png" class="index-logo" alt="">
        <p class="fr right-p">
          <nuxt-link :to="{name:'index'}" class="index-link"><i class="iconfont icon-diqiu"></i>&nbsp;首页</nuxt-link>
          <span v-if="isLogin == 'true'" class="login-info">
             <nuxt-link :to="{name:'personCenter'}">
                 <img class="pic-img" :src="userPicture" alt="">
                 <i class="iconfont icon-sanjiaodown"></i>
             </nuxt-link>
          </span>
          <span v-else>
            <nuxt-link :to="{name:'login'}" class="login-link"><i class="iconfont icon-suo"></i>&nbsp;登录</nuxt-link>
            <nuxt-link :to="{name:'register1'}" class="primary-btn reg-btn">注册</nuxt-link>
         </span>
          <nuxt-link :to="{name:'index'}" class="new-article"></nuxt-link>
        </p>
      </div>
    </div>
    <div class="main-content">
      <nuxt/>
    </div>
  </div>
</template>
<script>
  export default{
    data(){
      return {
        isLogin: false,//是否登录---
        userPicture: '',//头像
      }
    },
    mounted(){
      this.isLogin = sessionStorage.getItem('isLogin');
      if (sessionStorage.getItem('userInfo')) {
        this.userPicture = JSON.parse(sessionStorage.getItem('userInfo')).avatarImage.url;
      }
      console.log(this.isLogin, this.userPicture);
    }
  }
</script>
