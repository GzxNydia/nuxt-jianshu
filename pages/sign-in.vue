<template>
    <div class="sign">
        <!--logo-->
        <div class="logo">
             <nuxt-link to="/">
                 <img src="../assets/img/logo.png" alt="">
             </nuxt-link>
        </div>
        <!--登录表单-->
        <div class="main">
            <div class="title">
                <h4>
                    <nuxt-link to="sign-in" class="active">登录</nuxt-link>
                    <b>·</b>
                    <nuxt-link to="sign-up">注册</nuxt-link>
                </h4>
            </div>
            <div class="js-sign-in">
                <form action="/sign-in" method="post">
                    <div class="input-prepend">
                        <i class="fa fa-user"></i>
                        <input type="text" value="" placeholder="手机号或邮箱" class="top-radius">
                    </div>
                    <div class="input-prepend">
                        <i class="fa fa-lock"></i>
                        <input type="text" value="" placeholder="密码" class="bottom-radius">
                    </div>
                    <div class="remember">
                        <input type="checkbox">
                        &nbsp;<span>记住我</span>
                    </div>
                    <div class="help">
                        <nuxt-link to="/help">
                            登录遇到问题
                        </nuxt-link>
                    </div>
                    <input type="button" class="btn btn-primary" value="登录">
                </form>
                <div class="more-sign">
                    <p>社交账号登录</p>
                    <ul>
                        <li>
                            <a href="#">
                                <i class="fa fa-weibo"></i>
                            </a>
                        </li>
                        <li>
                            <a href="#">
                                <i class="fa fa-weixin"></i>
                            </a>
                        </li>
                        <li>
                            <a href="#">
                                <i class="fa fa-qq"></i>
                            </a>
                        </li>
                        <li class="other">
                            <a href="#">
                                其他
                            </a>
                        </li>
                    </ul>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    import '~/assets/css/sign.css'
    export default {
        name: "sign-in",
        layout:'sign',//指明当前页面所用的默认模板是layout文件夹下的sign.vue
        head(){
            return {
                title:'登录-简书',
                meta:[
                    {hide:'description',content:'登录页面'}
                ]
            }
        },
    }
</script>

<style scoped>

</style>