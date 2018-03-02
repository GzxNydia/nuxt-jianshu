<template>
    <div>
        <my-header></my-header>
        <div class="collection my-container" style="padding: 100px 0">
            <div class="row">
                <div class="col-8 main">
                    <div class="main-top">
                        <nuxt-link to="/u/123" class="avatar-collection">
                            <img src="~assets/img/default-avatar.jpg">
                        </nuxt-link>
                        <a class="btn btn-success" href="javascript:void(0)" :class="followObj" @click="isFollow"
                           @mouseover="noFollow" @mouseleave="beFollow">
                            <i class="fa" :class="iconObj" ref="icon"></i>
                            <span ref="followWord">关注</span>
                        </a>
                        <div class="btn btn-hollow">
                            投稿
                        </div>
                        <div class="title">
                            <nuxt-link class="name" to="/collection/123">
                                网易云音乐
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
                    <div id="list-container">
                        <!--动态组件-->
                        <component :is="currentTab" keep-alive></component>
                    </div>
                </div>
                <div class="col-4 aside">
                    <p class="title">专题公告</p>
                    <div class="description">
                        <p>
                            网易云音乐的评论背后都一个故事，让我们一起走进这些故事的背后，倾听那些未知何方的人和事。
                        </p>
                    </div>
                    <div class="share">
                        <span>分享到</span>
                        <a class="option" href="#">
                            <i class="fa fa-weibo"></i>
                        </a>
                        <a class="option">
                            <i class="fa fa-weixin"></i>
                        </a>
                    </div>
                    <div>
                        <p class="title">管理员</p>
                        <ul class="list collection-editor">
                            <li>
                                <nuxt-link to="/u/123" class="avatar">
                                    <img src="~assets/img/default-avatar.jpg">
                                </nuxt-link>
                                <nuxt-link to="/u/123" class="name">
                                    周九天
                                </nuxt-link>
                                <span class="tag">创建者</span>
                            </li>
                        </ul>
                    </div>
                    <div>
                        <div class="title">关注的人(14)</div>
                        <ul class="list collection-follower">
                            <li>
                                <nuxt-link to="/u/123" class="avatar">
                                    <img src="~assets/img/default-avatar.jpg">
                                </nuxt-link>
                            </li>
                            <li>
                                <nuxt-link to="/u/123" class="avatar">
                                    <img src="~assets/img/default-avatar.jpg">
                                </nuxt-link>
                            </li>
                            <li>
                                <nuxt-link to="/u/123" class="avatar">
                                    <img src="~assets/img/default-avatar.jpg">
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
    import NewComment from '../../components/collection/NewComment'
    import NewHot from '../../components/collection/NewHot'
    import NewArticle from '../../components/collection/NewArticle'
    export default {
        data () {
          return {
              currentTab:'NewComment',
              followObj: {
                  'follow': true,
                  'following': false
              },
              iconObj: {
                  'fa-plus-square-o': true,
                  'fa-check': false
              },
          }
        },
        methods:{
            toggleTab:function(tab){
              this.currentTab = tab;
            },
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
        },
        components:{
            myHeader,
            NewComment,
            NewHot,
            NewArticle
        }
    }
</script>
<style>

</style>