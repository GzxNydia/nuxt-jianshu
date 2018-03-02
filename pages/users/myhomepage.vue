<template>
    <div class="homepage">
        <my-header></my-header>
        <div class="my-container" style="padding:100px 0">
            <div class="row">
                <div class="col-8">
                    <div class="comment-placeholder clearfix">
                        <div class="author">
                            <div class="avatar" style="">
                                <img src="../../assets/img/default-avatar.jpg" alt="">
                            </div>
                            <div class="info">
                                <div class="name">
                                    测试用户
                                </div>
                                <ul class="meta">
                                    <li><p>212</p><nuxt-link to="/users/123/followers"">关注></nuxt-link></li>
                                    <li><p>100</p><nuxt-link to="/users/123/following"">粉丝></nuxt-link></li>
                                    <li><p>35</p><nuxt-link to="/users/myhomepage"">文章></nuxt-link></li>
                                    <li><p>5000</p><a href="javascript:void(0)">字数></a></li>
                                    <li><p>11</p><a href="javascript:void(0)">收获喜欢></a></li>
                                </ul>
                            </div>
                            <div class="sendBtn">
                                <a class="btn send" href="javascript:void(0)">
                                    <span>发简信</span>
                                </a>
                                <a class="btn" href="javascript:void(0)" :class="followObj" @click="isFollow"
                                   @mouseover="noFollow" @mouseleave="beFollow">
                                    <i class="fa" :class="iconObj" ref="icon"></i>
                                    <span ref="followWord">关注</span>
                                </a>
                            </div>
                        </div>
                    </div>
                    <ul class="trigger-menu">
                        <li :class="{active:currentTab == 'myArticle'}">
                            <a href="javascript:void(0)" @click="toggleTab('myArticle')">
                                <i class="fa fa-edit"></i>
                                文章
                            </a>
                        </li>
                        <li :class="{active:currentTab == 'myNew'}">
                            <a href="javascript:void(0)" @click="toggleTab('myNew')">
                                <i class="fa fa-bell"></i>
                                动态
                            </a>
                        </li>
                        <li :class="{active:currentTab == 'myComment'}">
                            <a href="javascript:void(0)" @click="toggleTab('myComment')">
                                <i class="fa fa-compress"></i>
                                最新评论
                            </a>
                        </li>
                        <li :class="{active:currentTab == 'myHot'}">
                            <a href="javascript:void(0)" @click="toggleTab('myHot')">
                                <i class="fa fa-fire"></i>
                                热门
                            </a>
                        </li>
                    </ul>
                    <div id="list-container">
                        <!--动态组件-->
                        <component :is="currentTab" keep-alive></component>
                    </div>
                </div>
                <div class="col-4 aside">
                    <div class="title">个人介绍</div>
                    <a class="function-btn" href="javascript:void(0)" @click="showText = true"><i class="fa fa-pencil"></i>编辑</a>
                    <div v-if="showText">
                        <textarea></textarea>
                        <div class="btn btn-hollow">保存</div>
                        <a class="cancel-info"  href="javascript:void(null);" @click="showText = false">取消</a>
                    </div>
                    <ul class="list user-dynamic">
                        <li>
                            <nuxt-link to="/users/123/collection">
                                <i class="fa fa-book"></i>
                                <span>他关注的专题/文集</span>
                            </nuxt-link>
                        </li>
                        <li>
                            <nuxt-link to="/users/123/like">
                                <i class="fa fa-heart-o"></i>
                                <span>他喜欢的文章</span>
                            </nuxt-link>
                        </li>
                    </ul>
                    <div>
                        <!--创建的专题-->
                        <div class="title">
                            他创建的专题
                        </div>
                        <nuxt-link to="/collection/new" class="function-btn new-collection-btn">
                            <i class="fa fa-plus"></i><span>新建专题</span>
                        </nuxt-link>
                        <ul class="list">
                            <li>
                                <nuxt-link to="/collection/123" class="avatar-collection">
                                    <img src="~assets/img/movie.jpg">
                                </nuxt-link>
                                <nuxt-link to="/collection/123" class="name">
                                    朱焘源值班报告
                                </nuxt-link>
                            </li>
                        </ul>
                        <!--管理的专题-->
                        <div class="title">
                            他管理的专题
                        </div>
                        <ul class="list">
                            <li>
                                <nuxt-link to="/collection/123" class="avatar-collection">
                                    <img src="~assets/img/movie.jpg">
                                </nuxt-link>
                                <nuxt-link to="/collection/123" class="name">
                                    朱焘源值班报告
                                </nuxt-link>
                            </li>
                        </ul>
                        <!--创建的文集-->
                        <div class="title">
                            他创建的文集
                        </div>
                        <ul class="list">
                            <li>
                                <nuxt-link to="/note/123" class="avatar-collection">
                                    <i class="fa fa-book"></i>
                                </nuxt-link>
                                <nuxt-link to="/note/123" class="name">
                                    朱焘源值班报告
                                </nuxt-link>
                            </li>
                        </ul>
                    </div>
                </div>
            </div>

        </div>
    </div>
</template>

<script>
    import myHeader from '../../components/myHeader'
    import MyArticle from '../../components/users/myArticle'
    import MyNew from '../../components/users/myNew'
    import MyComment from '../../components/users/myComment'
    import MyHot from '../../components/users/myHot'
    export default {
        name: 'myhomepage',
        components: {
            myHeader,
            MyArticle,
            MyNew,
            MyHot,
            MyComment
        },
        data() {
            return {
                currentTab:'myArticle',
                followObj: {
                    'follow': true,
                    'following': false
                },
                iconObj: {
                    'fa-plus-square-o': true,
                    'fa-check': false
                },
                showText:false
            }
        },
        methods: {
            isFollow: function () {
                this.followObj.follow = !this.followObj.follow;
                this.followObj.following = !this.followObj.following;
                this.iconObj['fa-plus-square-o'] = !this.iconObj['fa-plus-square-o'];
                this.iconObj['fa-check'] = !this.iconObj['fa-check'];
                let word = this.$refs.followWord.innerHTML;
                this.$refs.followWord.innerHTML = word == '关注' ? '已关注' : '关注';
            },
            noFollow: function () {
                let word = this.$refs.followWord.innerHTML;
                if (word == '已关注') {
                    this.$refs.followWord.innerHTML = '取消关注';
                    this.$refs.icon.className = 'fa fa-close';
                }
            },
            beFollow: function () {
                let word = this.$refs.followWord.innerHTML;
                if (word == '取消关注') {
                    this.$refs.followWord.innerHTML = '已关注';
                    this.$refs.icon.className = 'fa fa-check';

                }
            },
            toggleTab:function(tab){
                this.currentTab = tab;
            }
        }
    }
</script>

<style scoped>
    .homepage .col-8 .avatar {
        width: 80px;
        height: 80px;
        display: inline-block;
        margin-right: 15px;
        float: left;
        margin-bottom: 30px;
    }

    .homepage .col-8 .info {
        vertical-align: middle;
        float: left;
        margin-bottom: 30px;
    }

    .homepage .col-8 .info .name {
        width: 100%;
        height: 30px;
        font-size: 21px;
        font-weight: 700;
        background-color: #fff;
    }

    .homepage .col-8 .info .meta {
        width: 100%;
        height: 43px;
        display: flex;
        font-size: 12px;
        background-color: #fff;
    }

    .homepage .col-8 .info .meta li {
        padding-right: 7px;
        border-right: 1px solid #f0f0f0;
        margin-right: 7px;
        color: #969696;
    }

    .homepage .col-8 .info .meta li:last-child {
        border-right: none;
    }

    .homepage .col-8 .info .meta li p {
        font-size: 16px;
        margin-bottom: -3px;
        color: #333;
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
    .homepage .author .sendBtn {
        padding-top: 20px;
    }
    .homepage .author .btn {
        width: 100px;
        padding: 8px 0;
        box-shadow: none;
        font-size: 15px;
    }
    .homepage .author .send {
        border: 1px solid rgba(59, 194, 29, .7);
        color: #42c02e !important;
        font-size: 15px;
        border-radius: 20px;
        padding: 6px 7px;
        margin-right: 20px;
    }
    .homepage .author .follow {
        background: #42c02e;
        color: white !important;
        font-size: 15px;
        border-radius: 20px;
        padding: 6px 7px;
    }
    .homepage .author .following {
        background: #fff;
        color: #969696 !important;
        border: 1px solid #ccc;
        font-size: 15px;
        border-radius: 20px;
        padding: 6px 7px;
    }
    #list-container{
        margin-top: 20px;
    }
    .homepage .col-4 textarea {
        width: 100%;
        height: 100px;
        margin-bottom: 10px;
        padding: 10px 15px;
        font-size: 15px;
        border: 1px solid #c8c8c8;
        border-radius: 4px;
        background-color: hsla(0, 0%, 71%, .1);
        display: block;
        resize: none;
        outline-style: none;
    }
    .homepage .col-4 .cancel-info{
        color: #969696!important;
        font-size: 14px;
        margin-left: 20px;
    }
    .homepage .col-4 .cancel-info:hover{
        color: #333!important;
    }
    .homepage  .aside .title {
        float: left;
        margin-bottom: 10px;
        font-size: 14px;
        color: #969696;
    }
    .homepage  .aside .function-btn {
        float: right;
        font-size: 13px;
        color: #969696;
    }
    .homepage .aside .title {
        float: left;
        margin-bottom: 10px;
        font-size: 14px;
        color: #969696;
    }
    .homepage .aside .description {
        position: relative;
        margin-bottom: 20px;
        padding: 0 0 16px;
        text-align: left;
        font-size: 14px;
        border-bottom: 1px solid #f0f0f0;
        clear: both;
        word-break: break-word!important;
        word-break: break-all;
    }
    .homepage .aside .share {
        margin-bottom: 20px;
        padding-bottom: 20px;
        border-bottom: 1px solid #f0f0f0;
        line-height: 30px;
    }
    .homepage .aside .share span {
        font-size: 14px;
        vertical-align: middle;
    }
    .homepage .aside .share .option {
        margin-left: 10px;
        color: #333;
    }
    .homepage .aside .share i {
        font-size: 22px;
        vertical-align: middle;
    }
    .homepage .aside .list {
        margin-bottom: 20px;
        padding-bottom: 10px;
        list-style: none;
        border-bottom: 1px solid #f0f0f0;
        clear: both;
    }
    .homepage .aside .list li {
        margin-bottom: 10px;
    }
    .homepage .aside .list li a {
        display: inline-block;
    }
    .homepage .aside .avatar, .homepage .aside .avatar-collection {
        margin-right: 5px;
        width: 32px;
        height: 32px;
    }
    .homepage .aside a, .homepage .aside a:hover {
        color: #3194d0;
    }
    .homepage .aside .name {
        position: relative;
        max-width: 236px;
        vertical-align: middle;
        top: 1px;
        font-size: 14px;
        color: #333;
    }
    .homepage .aside .tag {
        padding: 1px 3px;
        margin-left: 2px;
        border-radius: 3px;
        font-size: 12px;
        color: #969696;
        border: 1px solid #969696;
    }
    .homepage .aside .list {
        margin-bottom: 20px;
        padding-bottom: 10px;
        list-style: none;
        border-bottom: 1px solid #f0f0f0;
        clear: both;
    }
    .homepage .aside .list.collection-follower li {
        display: inline-block;
    }
    .homepage .aside .list.collection-follower li:first-child {
        margin-left: -3px;
    }
    .homepage .aside .list li {
        margin-bottom: 10px;
    }
    .homepage .aside .list.collection-follower li a {
        margin-right: -10px;
    }
    .homepage .aside .list.collection-follower li img {
        border: 3px solid #fff;
        background-color: #fff;
    }
    .homepage.aside .title {
        float: left;
        margin-bottom: 10px;
        font-size: 14px;
        color: #969696;
    }
    .homepage .aside .function-btn {
        float: right;
        font-size: 13px;
        color: #969696;
    }
    .homepage.aside .description, .homepage .aside .new-collection-block {
        position: relative;
        margin-bottom: 16px;
        padding: 0 0 16px;
        text-align: left;
        font-size: 0;
        border-bottom: 1px solid #f0f0f0;
        clear: both;
        word-break: break-word!important;
        word-break: break-all;
    }
    .homepage .aside .description .js-intro, .homepage .aside .new-collection-block .js-intro {
        margin-bottom: 10px;
        line-height: 20px;
        font-size: 14px;
    }
    .homepage .aside .user-dynamic {
        padding-bottom: 6px;
    }
    .homepage .aside .list {
        margin-bottom: 16px;
        padding-bottom: 16px;
        list-style: none;
        border-bottom: 1px solid #f0f0f0;
        clear: both;
    }
    .homepage .aside .list li {
        margin-bottom: 10px;
    }
    .homepage .aside .list li a {
        display: inline-block;
    }
    .homepage .aside .user-dynamic a {
        font-size: 14px;
        color: #333;
        line-height: 30px;
    }
    .homepage .aside a, .person .aside a:hover {
        color: #3194d0;
    }
    .homepage .aside .list li a i {
        vertical-align: middle;
        margin-right: 5px;
    }
    .homepage .aside .user-dynamic i {
        margin-right: 10px;
        font-size: 20px;
        vertical-align: middle;
    }
    .homepage.aside .user-dynamic span {
        vertical-align: middle;
    }
    .homepage .aside .title {
        float: left;
        margin-bottom: 10px;
        font-size: 14px;
        color: #969696;
    }
    .homepage .aside .new-collection-btn {
        font-size: 13px;
        color: #42c02e!important;
    }
    .homepage .aside .function-btn {
        float: right;
        font-size: 13px;
        color: #969696;
    }
    .homepage .aside .new-collection-btn i {
        padding-right: 2px;
    }
    .homepage .aside .list {
        margin-bottom: 16px;
        padding-bottom: 16px;
        list-style: none;
        border-bottom: 1px solid #f0f0f0;
        clear: both;
    }
    .homepage .aside .avatar, .person .aside .avatar-collection {
        margin-right: 5px;
        width: 32px;
        height: 32px;
    }
    .avatar-collection img {
        width: 100%;
        height: 100%;
        border: 1px solid #ddd;
        border-radius: 10%;
    }
    .homepage .aside .name {
        position: relative;
        max-width: 236px;
        vertical-align: middle;
        top: 1px;
        font-size: 14px;
        color: #333;
    }
    .homepage .aside .list li a i {
        color:#969696;
        font-size:25px;
        vertical-align: middle;
        margin-right: 5px;
    }
</style>