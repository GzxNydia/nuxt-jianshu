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
                    <nuxt-link to="sign-in" >登录</nuxt-link>
                    <b>·</b>
                    <nuxt-link to="sign-up" class="active">注册</nuxt-link>
                </h4>
            </div>
            <div class="js-sign-up">
                <form action="/sign-up" method="post">
                    <div class="input-prepend">
                        <i class="fa fa-user"></i>
                        <input type="text" value="" placeholder="你的昵称" class="top-radius">
                    </div>
                    <div class="input-prepend">
                        <i class="fa fa-mobile-phone"></i>
                        <input type="text" value="" placeholder="手机号">
                    </div>
                    <div class="input-prepend ssm">
                        <i class="fa fa-shield"></i>
                        <input type="text" value="" placeholder="手机验证码">
                        <a href="#" class="btn btn-success send-ssm">发送验证码</a>
                    </div>
                    <div class="input-prepend">
                        <i class="fa fa-lock"></i>
                        <input type="text" value="" placeholder="设置密码" class="bottom-radius">
                    </div>
                    <input type="button" class="btn btn-success reg-btn" value="注册">
                    <p class="sign-up-msg">
                        点击 “注册” 即表示您同意并愿意遵守简书<br>
                        <a href="#">用户协议 </a>和 <a href="#">隐私政策</a> 。
                    </p>
                </form>
                <div class="more-sign">
                    <p>社交账号直接注册</p>
                    <ul>
                        <li>
                            <a href="#">
                                <i class="fa fa-weibo"></i>
                            </a>
                        </li>
                        <li>
                            <a href="#">
                                <i class="fa fa-qq"></i>
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
        name: "sign-up",
        layout:'sign',//指明当前页面所用的默认模板是layout文件夹下的sign.vue
        head(){
            return {
                title:'注册-简书',
                meta:[
                    {hide:'description',content:'注册页面'}
                ]
            }
        },
    }
</script>

<style scoped>

</style>