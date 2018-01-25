<template>
  <section>
    <!--<h1 class="title">-->
    <!--{{ error.statusCode }}-->
    <!--</h1>-->
    <!--<h2 class="info">-->
    <!--{{ error.message }}11111111-->
    <!--</h2>-->
    <div class="container">
      <div class="logoImg">
        <img src="../assets/img/error.png" alt="">
      </div>
      <img src="../assets/img/404.png" alt="">
      <h3><strong>你要找的页面不存在</strong></h3>
      <p>可能是因为您的链接地址有误、该文章已经被作者删除或转为私密状态。</p>
      <div>
        <nuxt-link class="button" to="/" v-if="error.statusCode === '404'">
          <input class="btn btn-success reg-btn" type="button" value="返回简书首页">
        </nuxt-link>
      </div>
    </div>
    <ul class="imgRouter">
      <li>
        <a href="#">
          <i class="fa fa-mobile-phone"></i>
        </a>
        免费下载简书APP

      </li>
      <li>
        <a href="#">
          <i class="fa fa-weibo"></i>
        </a>
        关注简书官方微博
      </li>
      <li>
        <a href="#">
          <i class="fa fa-weibo"></i>
        </a>
        关注简书官方微博
      </li>
    </ul>
    </section>
</template>
<script>
    import 'assets/css/error.css'
    export default {
        props: ['error']
    }
</script>

<style scoped>
  .title
  {
    margin-top: 15px;
    font-size: 5em;
  }
  .info
  {
    font-weight: 300;
    color: #9aabb1;
    margin: 0;
  }
  .button
  {
    margin-top: 50px;
  }
</style>