<template>
    <div>
        <nav class="navbar navbar-default nav-fixed-top">
            <div class="width-limit">
               <!--logo-->
                <nuxt-link to="/" class="navlogo">
                    <img src="../assets/img/nav-logo.png" alt="">
                </nuxt-link>
                <!--写文章-->
                <nuxt-link to="/creat" class="write-btn btn">
                    <i class="fa fa-edit"></i>
                    写文章
                </nuxt-link>
                <!--登录和注册按钮-->
                <nuxt-link to="/sign-up" class="btn sign-up" href="">注册</nuxt-link>
                <nuxt-link to="/sign-in" class="btn sign-in" href="">登录</nuxt-link>

                <!--如果用户登录 name显示用户头像-->
                <div  style="display: none" class="user"  @mouseover="userShow=true" @mouseleave="userShow=false">
                    <div class="drop-down">
                        <nuxt-link to="/user" class="avatar">
                            <img src="../assets/img/default-avatar.jpg" alt="">
                        </nuxt-link>
                    </div>
                    <div class="drop-menu"  v-show="userShow">
                        <ul>
                            <li>
                                <nuxt-link to="/">
                                    <i class="fa fa-user"></i>
                                    我的主页
                                </nuxt-link>
                            </li>
                            <li>
                                <nuxt-link to="/">
                                    <i class="fa fa-bookmark"></i>
                                    收藏的文章
                                </nuxt-link>
                            </li>
                            <li>
                                <nuxt-link to="/">
                                    <i class="fa fa-heart"></i>
                                    喜欢的文章
                                </nuxt-link>
                            </li>
                            <li>
                                <nuxt-link to="/">
                                    <i class="fa fa-cog"></i>
                                    设置
                                </nuxt-link>
                            </li>
                            <li>
                                <nuxt-link to="/">
                                    <i class="fa fa-sign-out"></i>
                                    退出
                                </nuxt-link>
                            </li>
                        </ul>
                    </div>

                </div>
                <!--导航-->
                <div class="my-container">
                    <ul class="nav-list">
                        <li class="active">
                            <nuxt-link to="/" >
                                <i class="fa fa-compass"></i>
                                <span>发现</span>
                            </nuxt-link>
                        </li>
                        <li>
                            <nuxt-link to="/">
                                <i class="fa fa-bookmark-o"></i>
                                <span>关注</span>
                            </nuxt-link>
                        </li>
                        <li class="notify" @mouseover="msgShow=true" @mouseleave="msgShow=false">
                            <nuxt-link to="/" >
                                <i class="fa fa-bell-o"></i>
                                <span>消息</span>
                            </nuxt-link>
                            <div class="drop-menu" v-show="msgShow">
                                <ul>
                                    <li>
                                        <nuxt-link to="/">
                                            <i class="fa fa-comment-o"></i>
                                              评论&emsp;&emsp;
                                        </nuxt-link>
                                    </li>
                                    <li>
                                        <nuxt-link to="/">
                                            <i class="fa fa-envelope-o"></i>
                                              简信&emsp;&emsp;
                                        </nuxt-link>
                                    </li>
                                    <li>
                                        <nuxt-link to="/">
                                            <i class="fa fa-paper-plane-o"></i>
                                            投稿请求
                                        </nuxt-link>
                                    </li>
                                    <li>
                                        <nuxt-link to="/">
                                            <i class="fa fa-heart-o"></i>
                                            喜欢和赞
                                        </nuxt-link>
                                    </li>
                                    <li>
                                        <nuxt-link to="/">
                                            <i class="fa fa-user-o"></i>
                                              关注&emsp;&emsp;
                                        </nuxt-link>
                                    </li>
                                </ul>
                            </div>
                        </li>
                        <li class="search">
                            <form method="post">
                                <input type="text" placeholder="搜索" @focus="bgShow=true" @blur="bgShow=false">
                                <nuxt-link to="/search" href="" class="search-btn" :class="{active:bgShow}">
                                    <i class="fa fa-search"></i>
                                </nuxt-link>
                            </form>
                        </li>
                    </ul>
                </div>
            </div>
        </nav>
    </div>
</template>

<script>
    export default {
        name: "my-header",
        data(){
            return {
                userShow:false,
                msgShow:false,
                bgShow:false
            }
        }
    }
</script>

<style scoped>
    nav {
        height: 56px;
        width: 100%;
    }
    .navbar {
        padding: 0;
        border-bottom: 1px solid #f0f0f0;
        margin-bottom: 20px;
        background-color: white;
    }
    nav.nav-fixed-top{
        position: fixed;
        top: 0;
        z-index: 9999;
    }
    nav .width-limit{
        width: 1440px;
        min-width: 768px;
        margin: 0 auto;
    }
    nav .navlogo{
        float: left;
        height: 56px;
        padding: 0;
    }
    nav .navlogo img{
        height: 100%;
    }
    nav .write-btn{
        float: right;
        width: 100px;
        height: 40px;
        line-height: 24px;
        font-size: 14px;
        margin: 7px 15px 0;
        background-color: #ea6f5a;
        color: #fff!important;
        border-radius: 20px;
    }
    nav a.sign-in{
        float: right;
        margin: 8px 6px 0 10px;
        line-height: 24px;
        font-size: 15px;
        color: #969696!important;
    }
    nav a.sign-in:active{
        box-shadow: none;
    }
    nav a.sign-up{
        float: right;
        width: 80px;
        height: 38px;
        margin: 8px 6px 0 10px;
        line-height: 24px;
        font-size: 15px;
        border: 1px solid #ea6f5a;
        border-radius: 20px;
        color: #ea6f5a!important;
    }
    nav a.sign-up:hover {
        background-color: rgba(254,247,246);
    }
    nav a.sign-up:active{
        box-shadow: none;
    }
   nav .user{
       float: right;
       position: relative;
   }
    nav .user .avatar{
        width: 40px;
        height: 40px;
        display: block;
        margin: 8px 28px 8px 20px;
        position: relative;
    }
    nav .user:hover{
        background-color: #f5f5f5;
    }
    nav .user .avatar::after{
        content: "";
        position: absolute;
        top: 18px;
        right: -14px;
        border-left: 5px solid transparent;
        border-right: 5px solid transparent;
        border-top: 6px solid #999;

    }
    nav .user .avatar img{
        width: 100%;
        height: 100%;
        border-radius: 50%;
    }
    nav .user .drop-menu{
        position: absolute;
        left: 0;
        min-width: 160px;
        box-shadow: 0 0 8px rgba(0,0,0,.1);
        font-size: 14px;

    }
    nav .user .drop-menu ul{
        border: 1px solid #ccc;
        padding: 10px 0;
        /*text-align: center;*/
        margin: 0;
    }
    nav .user .drop-menu ul li a{
        display: block;
        padding: 10px;
    }
    nav .user .drop-menu ul li a:hover{
        background-color: #f5f5f5;
    }
    nav .user .drop-menu ul li i{
        margin-right: 15px;
        color: #ea6f5a;
        font-size: 18px;
    }
    nav .nav-list:after{
       content: "";
        clear: both;
    }
    nav .nav-list{
        margin: 0 -15px!important;
        padding: 0;
    }
    nav .nav-list>li {
        float: left;
        margin-right: 5px;
    }
    nav .nav-list>li:hover {
        background-color: #f5f5f5;
    }
    nav .nav-list>li>a {
        display: block;
        height: 55px;
        padding: 15px;
        margin-right: 15px;
        font-size: 17px;
        text-align: center;
    }
    nav .nav-list>li>a>i {
        margin-right: 7px;
        font-size: 20px;
    }
    nav .nav-list>li.active{
        color: #ea6f5a;
        background-color: white;
    }
    nav .nav-list .notify{
        position: relative;

        z-index: 9999;
    }
    nav .nav-list .notify .drop-menu{
        position: absolute;
        left: 0;
        top: 56px;
        min-width: 160px;
        box-shadow: 0 0 8px rgba(0,0,0,.1);
        font-size: 15px;
        background-color: white;
    }
    nav .nav-list .notify .drop-menu ul{
        border: 1px solid #ccc;
        padding: 10px 0;
        margin:0;
    }
    nav .nav-list .notify .drop-menu ul li a{
        padding: 10px 20px;
        margin: 0;
        display: block;
        line-height: 30px;
    }
    nav .nav-list .notify .drop-menu ul li a:hover{
        background-color: #f5f5f5;
    }
    nav .nav-list .notify .drop-menu ul li i{
        margin-right: 15px;
        color: #ea6f5a;
        font-size: 18px;
        float: left;
        line-height: 30px;
    }
    nav .nav-list .search {
        padding-left: 15px;
        background-color: #fff;
    }
    nav .nav-list .search:hover {
        background-color: #fff;
    }
    nav .nav-list .search form {
        margin-top: 9px;
        position: relative;
    }
    nav .nav-list .search form input{
        width: 240px;
        height: 38px;
        border: none;
        background-color: rgba(238,238,238,.5);
        border-radius: 20px;
        padding: 0 30px 0 20px;
        font-size: 13px;
        transition: width .3s ease-in;
    }

    nav .nav-list .search form input:focus{
        width: 320px;

    }
    nav .nav-list .search form a.search-btn{
        position: absolute;
        right: 5px;
        top: 5px;
        display: block;
        width: 30px;
        height: 30px;
        text-align: center;
        line-height: 30px;
    }
    nav .nav-list .search form a.active{
        background-color: #969696;
        border-radius: 50%;
        color: white!important;
    }
    @media (max-width: 1440px) {
        nav .nav-list>li>a i {
            display: none;
        }
        nav .nav-list .search form input{
            width: 160px;
        }
        nav .nav-list .search form input:focus{
            width: 320px;

        }
    }
    @media (max-width: 1080px) {
        nav .nav-list>li>a i {
            display: block;
        }
        nav .nav-list>li>a span{
            display: none;
        }
        nav .nav-list .search form input:focus{
            width: 160px;
        }
    }
    @media (max-width: 820px) {
        nav .nav-list {
            display: none;
        }
    }
</style>