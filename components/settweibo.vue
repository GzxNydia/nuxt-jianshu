<template>
    <div class="main">
        <img src="../assets/img/weibo.png"
             class="weibo-auth-img">
        <div class="certification">
            <div class="title">简书新浪微博联合认证</div>
            <span>简书推荐作者</span>
            <ul>
                <li>
                    <i class="fa fa-check"></i>
                    简书帐号注册超过 30 天
                </li>
                <li>
                    <i class="fa fa-check"></i>
                    简书帐号绑定新浪微博帐号
                </li>
                <li>
                    <i class="fa fa-check"></i>
                    绑定手机号码
                </li>
                <li><i class="fa fa-check"></i>
                    在简书发表文章字数达到 20000 字
                </li>
                <li>
                    <i class="fa fa-check"></i>
                    在简书收获喜欢数达到 2000 个
                </li>
            </ul> <!----></div>
        <div class="certification">
            <div class="title">简书新浪微博联合认证</div>
            <span>简书专题运营者</span>
            <ul>
                <li><i class="fa fa-check"></i>
                    简书帐号注册超过 30 天
                </li>
                <li><i class="fa fa-minus"></i>
                    简书帐号绑定新浪微博帐号
                </li>
                <li><i class="fa fa-check"></i>
                    绑定手机号码
                </li>
                <li><i class="fa fa-minus"></i>
                    在简书参与编辑的专题收获订阅总数达到 1000 个
                </li>
            </ul> <!----></div>
        <!---->
    </div>
</template>

<script>
    export default {
        name: 'settweibo'
    }
</script>

<style scoped>
    .main .weibo-auth-img {
        margin: 0 0 30px -12px;
        width: 450px;
        height: 216px;
    }

    .main .title {
        font-size: 15px;
        font-weight: 700;
        display: inline-block;
        vertical-align: middle;
    }

    .main span {
        margin: 0 20px 0 6px;
        font-size: 14px;
        vertical-align: middle;
        color: #969696;
    }

    .main .certification ul {
        margin: 25px 0;
    }

    .main .certification li {
        font-size: 15px;
        line-height: 30px;
    }

    .main .certification {
        margin-bottom: 40px;
    }
    .fa-check{
        color: #42c02e;
        font-size: 15px;
    }
</style>