<template>
    <div class="my-container">
        <my-header></my-header>
        <div class="collection my-container" style="padding: 100px 0">
            <div class="row">
                <div class="col-4" style="border-right: 1px solid #f0f0f0;padding: 0;">
                    <div class="followTitle">
                        <div>
                            <span ref="val0" @click="showVal=!showVal">全部关注</span>
                            <span class="followDown">
                                <i class="fa fa-caret-down" @click="showVal=!showVal"></i>
                                <div v-if="showVal"></div>
                                <ul class="followMeau" v-if="showVal">
                                    <li @click="showValue(0)"><a href="javascript:void(0)" ref="value0">全部关注</a></li>
                                    <li @click="showValue(1)"><a href="javascript:void(0)" ref="value1">只看作者</a></li>
                                    <li @click="showValue(2)"><a href="javascript:void(0)" ref="value2">只看专题</a></li>
                                    <li @click="showValue(3)"><a href="javascript:void(0)" ref="value3">只看文集</a></li>
                                </ul>
                            </span>
                        </div>
                        <div>
                            <i class="fa fa-address-book"></i>
                            <span style="margin-left: 5px">添加关注</span>
                        </div>
                    </div>
                    <ul>
                        <li v-for="index in 3" :class="activeColor == index?'activeColor':''" @click="changeActive(activeColor=index)">
                            <span class="avatar">
                                <img src="~assets/img/default-avatar.jpg">
                            </span>
                            <span to="/" class="name">
                                测试用户
                            </span>
                        </li>
                    </ul>

                </div>
                <div class="col-8 main">
                    <div v-if="activeColor==1">
                        <div class="main-top">
                            <nuxt-link to="/" class="avatar-collection">
                                <img src="~assets/img/default-avatar.jpg">
                            </nuxt-link>
                            <div class="btn btn-hollow follow">
                                <nuxt-link to="/collection/123">
                                    个人主页 <i class="fa fa-angle-right"></i>
                                </nuxt-link>
                            </div>
                            <div class="btn btn-hollow">
                                发简信
                            </div>
                            <div class="title">
                                <nuxt-link class="name" to="/collection/123">
                                    测试用户1
                                </nuxt-link>
                            </div>
                            <div class="info">
                                收录了30篇文章 · 13人关注
                            </div>
                        </div>
                        <!---->
                        <ul class="trigger-menu">
                            <li :class="{active:currentTab == 'NewComment'}">
                                <a href="javascript:void(0)" @click="toggleTab('NewComment')">
                                    <i class="fa fa-comment"></i>
                                    最新评论
                                </a>
                            </li>
                            <li :class="{active:currentTab == 'NewArticle'}">
                                <a href="javascript:void(0)" @click="toggleTab('NewArticle')">
                                    <i class="fa fa-weibo"></i>
                                    最新收录
                                </a>
                            </li>
                            <li :class="{active:currentTab == 'NewHot'}">
                                <a href="javascript:void(0)" @click="toggleTab('NewHot')">
                                    <i class="fa fa-fire"></i>
                                    热门
                                </a>
                            </li>
                        </ul>
                        <div id="list-container" style="margin-top: 20px">
                            <!--动态组件-->
                            <component :is="currentTab" keep-alive></component>
                        </div>
                    </div>
                    <div v-if="activeColor==2">
                        <div class="main-top">
                            <nuxt-link to="/collection/123" class="avatar-collection">
                                <img src="~assets/img/default-avatar.jpg">
                            </nuxt-link>
                            <div class="btn btn-hollow follow">
                                <nuxt-link to="/collection/123">
                                    个人主页 <i class="fa fa-angle-right"></i>
                                </nuxt-link>
                            </div>
                            <div class="btn btn-hollow">
                                发简信
                            </div>
                            <div class="title">
                                <nuxt-link class="name" to="/collection/123">
                                    测试用户2
                                </nuxt-link>
                            </div>
                            <div class="info">
                                收录了40篇文章 · 14人关注
                            </div>
                        </div>
                        <!---->
                        <ul class="trigger-menu">
                            <li :class="{active:currentTab == 'NewComment'}">
                                <a href="javascript:void(0)" @click="toggleTab('NewComment')">
                                    <i class="fa fa-comment"></i>
                                    最新评论
                                </a>
                            </li>
                            <li :class="{active:currentTab == 'NewArticle'}">
                                <a href="javascript:void(0)" @click="toggleTab('NewArticle')">
                                    <i class="fa fa-weibo"></i>
                                    最新收录
                                </a>
                            </li>
                            <li :class="{active:currentTab == 'NewHot'}">
                                <a href="javascript:void(0)" @click="toggleTab('NewHot')">
                                    <i class="fa fa-fire"></i>
                                    热门
                                </a>
                            </li>
                        </ul>
                        <div id="list-container" style="margin-top: 20px">
                            <!--动态组件-->
                            <component :is="currentTab" keep-alive></component>
                        </div>
                    </div>
                    <div v-if="activeColor==3">
                        <div class="main-top">
                            <nuxt-link to="/collection/123" class="avatar-collection">
                                <img src="~assets/img/default-avatar.jpg">
                            </nuxt-link>
                            <div class="btn btn-hollow follow">
                                <nuxt-link to="/">
                                    个人主页 <i class="fa fa-angle-right"></i>
                                </nuxt-link>
                            </div>
                            <div class="btn btn-hollow">
                                发简信
                            </div>
                            <div class="title">
                                <nuxt-link class="name" to="/collection/123">
                                    测试用户3
                                </nuxt-link>
                            </div>
                            <div class="info">
                                收录了44篇文章 · 42人关注
                            </div>
                        </div>
                        <!---->
                        <ul class="trigger-menu">
                            <li :class="{active:currentTab == 'NewComment'}">
                                <a href="javascript:void(0)" @click="toggleTab('NewComment')">
                                    <i class="fa fa-comment"></i>
                                    最新评论
                                </a>
                            </li>
                            <li :class="{active:currentTab == 'NewArticle'}">
                                <a href="javascript:void(0)" @click="toggleTab('NewArticle')">
                                    <i class="fa fa-weibo"></i>
                                    最新收录
                                </a>
                            </li>
                            <li :class="{active:currentTab == 'NewHot'}">
                                <a href="javascript:void(0)" @click="toggleTab('NewHot')">
                                    <i class="fa fa-fire"></i>
                                    热门
                                </a>
                            </li>
                        </ul>
                        <div id="list-container" style="margin-top: 20px">
                            <!--动态组件-->
                            <component :is="currentTab" keep-alive></component>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    import myHeader from '~/components/myHeader'
    import NewComment from '~/components/collection/NewComment'
    import NewHot from '~/components/collection/NewHot'
    import NewArticle from '~/components/collection/NewArticle'
    export default {
        data(){
          return {
              currentTab:'NewComment',
              headCount:1,
              activeColor:1,
              showPop:false,
              showVal:false
          }
        },
        methods:{
            toggleTab:function(tab){
                this.currentTab = tab;
            },
            changeActive:function(index){
                console.log(index)
            },
            showValue:function(index){
                if(index == 0){
                    this.$refs.val0.innerHTML=this.$refs.value0.innerHTML
                }
                if(index == 1){
                    this.$refs.val0.innerHTML=this.$refs.value1.innerHTML
                }
                if(index == 2){
                    this.$refs.val0.innerHTML=this.$refs.value2.innerHTML
                }
                if(index == 3){
                    this.$refs.val0.innerHTML=this.$refs.value3.innerHTML
                }
                this.showVal=false
            }
        },
        components: {
            myHeader,
            NewComment,
            NewHot,
            NewArticle
        }
    }
</script>

<style scoped>
    .collection .row {
        padding-top:30px;
    }
    .collection .main .main-top {
        margin-bottom: 35px;
    }
    .collection .main .main-top .avatar-collection {
        float: left;
        width: 80px;
        height: 80px;
    }
    .avatar-collection img {
        width: 100%;
        height: 100%;
        border: 1px solid #ddd;
        border-radius: 10%;
    }
    .collection .main .main-top .follow, .collection .main .main-top .follow-cancel, .collection .main .main-top .follow-each, .collection .main .main-top .following {
        padding: 8px 0;
        width: 100px;
    }
    .collection .main .main-top .btn {
        float: right;
        margin: 23px 0 23px 16px;
        font-size: 15px;
    }
    .collection .main .main-top .btn-hollow {
        padding: 8px 0;
        width: 90px;
        font-weight: 400;
        line-height: normal;
        border-radius: 40px;
        background: none;
        color: #42c02e;
        border: 1px solid rgba(59,194,29,.7);
    }
    .collection .main .main-top .btn-hollow:hover {
        background: rgb(245,252,243);
    }
    .collection .main .main-top .btn {
        float: right;
        margin: 23px 0 23px 16px;
        font-size: 15px;
    }
    .collection .main .main-top .btn-success {
        color:#fff!important;
        background:#42c02e;
        border-radius: 40px;
    }
    .collection .main .main-top .btn-success:hover {
        background: rgb(61,185,34)!important;
    }
    .collection .main .main-top .title {
        padding: 10px 0 0 100px;
    }
    .collection .main .main-top .title .name {
        display: inline;
        font-size: 21px;
        font-weight: 700;
        vertical-align: middle;
    }
    .collection .col-8 .main-top .info {
        margin-top: 10px;
        padding-left: 100px!important;
        font-size: 14px;
        color: #969696!important;
    }
    .collection .col-4 .followTitle{
        display: flex;
        justify-content: space-between;
        border-bottom: 1px solid #f0f0f0;
        font-size: 14px;
        color: #333;
        padding: 20px 10px;
    }
    .collection .col-4 .followTitle>div{
        cursor: pointer;
    }
    .collection .col-4 .followTitle .followDown{
        position: relative;
        width: 15px;
        height: 15px;
        margin-left: 5px;
        display:inline-block;
        text-align:center;
        line-height: 15px;
        border-radius: 50%;
        background-color: #969696;
        color: #fff;
    }
    .collection .col-4 .followTitle .followDown div{
        position: absolute;
        width: 10px;
        height: 10px;
        transform: rotate(45deg);
        background-color: #fff;
        top:20px;
        border-left: 1px solid #969696;
        border-top: 1px solid #969696;
        z-index: 999;
    }
    .collection .col-4 .followTitle .followMeau{
        position: absolute;
        background-color: #fff;
        width: 130px;
        left: -60px;
        top:25px;
        border: 1px solid #969696;
    }
    .collection .col-4 .followTitle .followMeau li{
        color: #333;
        padding: 10px 20px;
    }
    .collection .col-4 .followTitle .followMeau li:hover{
        background-color: #f0f0f0;
    }
    .collection .main .followTitle span{
        margin: 0 5px;
    }
    .collection .col-4>ul>li{
        display: flex;
        width: 100%;
        height: 60px;
        padding: 10px 0;
    }
    .collection .col-4>ul>li span{
        margin-left: 10px;
        cursor: pointer;
    }
    .collection .col-4>ul>li:hover{
        background-color: #f0f0f0;
    }
    .collection .col-4>ul>li.activeColor{
        background-color: #f0f0f0;
    }
    .collection .col-4 .avatar{
        width: 40px;
        height: 40px;
    }
    .collection .col-4 .name{
        margin-left: 10px;
        line-height: 40px;
    }
    .trigger-menu {
        margin-bottom: 20px;
        border-bottom: 1px solid #f0f0f0;
        font-size: 0;
        list-style: none;
    }
    .trigger-menu li {
        position: relative;
        display: inline-block;
        padding: 8px 0;
        margin-bottom: -1px;
    }
    .trigger-menu a {
        padding: 13px 20px;
        font-size: 15px;
        font-weight: 700;
        color: #969696!important;
        line-height: 25px;
    }
    .trigger-menu i {
        margin-right: 5px;
        font-size: 17px;
    }
    .trigger-menu li.active {
        border-bottom: 2px solid #646464;
    }
    .trigger-menu .active a, .trigger-menu a:hover {
        color: #646464!important;
    }
    .trigger-menu li:after {
        content: "";
        position: absolute;
        left: 50%;
        bottom: -2px;
        width: 100%;
        opacity: 0;
        border-bottom: 2px solid #646464;
        -webkit-transform: translate(-50%) scaleX(0);
        transform: translate(-50%) scaleX(0);
        transition: .2s ease-in-out
    }
    .trigger-menu li:hover:after {
        opacity: 1;
        -webkit-transform: translate(-50%) scaleX(1);
        transform: translate(-50%) scaleX(1);
        transition: .2s ease-in-out
    }
</style>