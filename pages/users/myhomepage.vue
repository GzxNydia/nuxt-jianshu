<template>
    <div class="homepage">
        <my-header></my-header>
        <div class="my-container" style="padding:100px 0">
            <div class="row">
                <div class="col-8">
                    <div class="comment-placeholder">
                        <div class="author">
                            <div class="avatar" style="">
                                <img src="../../assets/img/default-avatar.jpg" alt="">
                            </div>
                            <div class="info">
                                <div class="name">
                                    测试用户
                                </div>
                                <ul class="meta">
                                    <li><p>212</p><a href="javascript:void(0)">关注></a></li>
                                    <li><p>100</p><a href="javascript:void(0)">粉丝></a></li>
                                    <li><p>35</p><a href="javascript:void(0)">文章></a></li>
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
                    <ul class="homeContent">
                        <li :class="actives[0].active" @click="conentChange(0)"
                            @mouseover="hoverenter(0)" @mouseleave="hoverleave(0)">
                            <i class="fa fa-book"></i><span>文章</span>
                            <div :class="actives[0].active" ref="act0"></div>
                        </li>
                        <li :class="actives[1].active" @click="conentChange(1)"
                            @mouseover="hoverenter(1)" @mouseleave="hoverleave(1)">
                            <i class="fa fa-book"></i><span>动态</span>
                            <div :class="actives[1].active" ref="act1"></div>
                        </li>
                        <li :class="actives[2].active" @click="conentChange(2)"
                            @mouseover="hoverenter(2)" @mouseleave="hoverleave(2)">
                            <i class="fa fa-book"></i><span>最新评论</span>
                            <div :class="actives[2].active" ref="act2"></div>
                        </li>
                        <li :class="actives[3].active" @click="conentChange(3)"
                            @mouseover="hoverenter(3)" @mouseleave="hoverleave(3)">
                            <i class="fa fa-book"></i><span>热门</span>
                            <div :class="actives[3].active" ref="act3"></div>
                        </li>
                    </ul>
                    <div v-if="actives[0].active != ''">
                        <my-article></my-article>
                    </div>
                    <div v-if="actives[1].active != ''">
                        <my-new></my-new>
                    </div>
                    <div v-if="actives[2].active != ''">
                        <my-comment></my-comment>
                    </div>
                    <div v-if="actives[3].active != ''">
                        <my-hot></my-hot>
                    </div>
                </div>
                <div class="col-4">
                    <div class="title-info">个人介绍</div>
                    <a class="function-btn" href="javascript:void(0)" @click="showText = true"><i class="fa fa-pencil"></i>编辑</a>
                    <div v-if="showText">
                        <textarea></textarea>
                        <div class="btn btn-hollow">保存</div>
                        <a class="cancel-info"  href="javascript:void(null);" @click="showText = false">取消</a>
                    </div>
                    <ul>
                        <li>
                            <i class="fa fa-heart"></i>
                            我关注的专题/文集/连载
                        </li>
                        <li>
                            <i class="fa fa-heart"></i>
                            我喜欢的文章
                        </li>
                    </ul>
                    <div class="addContent">
                        <p>我创建的专题</p>
                        <span>
                            <nuxt-link to="collections/new">
                                <i class="fa fa-plus"></i>
                                创建一个新专题
                            </nuxt-link>
                        </span>
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
                actives: [
                    {active: ''},
                    {active: ''},
                    {active: 'active'},
                    {active: ''},
                ],
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
            conentChange: function (index) {
                for (let i in this.actives) {
                    if (i == index) {
                        this.actives[i].active = 'active';
                    } else {
                        this.actives[i].active = '';
                    }
                }
            },
            hoverenter: function (index) {
                if (index == 0) {
                    this.$refs.act0.classList.add('active2');
                } else if (index == 1) {
                    this.$refs.act1.classList.add('active2');
                } else if (index == 2) {
                    this.$refs.act2.classList.add('active2');
                } else if (index == 3) {
                    this.$refs.act3.classList.add('active2');
                }
            },
            hoverleave: function (index) {
                if (index == 0) {
                    this.$refs.act0.classList.remove('active2');
                } else if (index == 1) {
                    this.$refs.act1.classList.remove('active2');
                } else if (index == 2) {
                    this.$refs.act2.classList.remove('active2');
                } else if (index == 3) {
                    this.$refs.act3.classList.remove('active2');
                }
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

    .homepage .col-8 .homeContent {
        width: 100%;
        display: flex;
        border-bottom: 1px solid #f0f0f0;
    }

    .homepage .col-8 .homeContent > li {
        padding: 13px 0 0 0;
        cursor: pointer;
        color: #969696;
    }

    .homepage .col-8 .homeContent > li.active {
        color: #333;
    }

    .homepage .homeContent > li:hover {
        color: #333;
    }

    .homepage .col-8 .homeContent > li > div {
        width: 0;
        height: 2px;
        margin: 0 auto;
        margin-top: 10px;
        background-color: #fff;
        transition: width .3s linear;
    }

    .homepage .col-8 .homeContent > li > div:hover {
        width: 100%;
        background-color: #333;
    }

    .homepage .col-8 .homeContent > li > div.active, .homepage .homeContent > li > div.active2 {
        width: 100%;
        background-color: #333;
    }

    .homepage .col-8 .homeContent > li > i {
        margin-right: 5px;
        padding-left: 20px;
    }

    .homepage .col-8 .homeContent > li > span {
        padding-right: 20px;
    }

    .homepage .col-4 ul {
        margin-top: 40px !important;
        border-top: 1px solid #f0f0f0;
        border-bottom: 1px solid #f0f0f0;
    }

    .homepage .col-4 ul li {
        padding: 10px;
        font-size: 14px;
    }

    .homepage .col-4 ul li > i {
        font-size: 18px;
        vertical-align: middle;
    }

    .homepage .col-4 .addContent {
        border-bottom: 1px solid #f0f0f0;
        font-size: 14px;
        padding: 10px;
        line-height: 20px;
    }

    .homepage .col-4 .addContent span p {
        margin-bottom: 0;
    }

    .homepage .col-4 .addContent span {
        font-size: 13px;
        color: #42c02e;
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

    .homepage .col-4 .title-info {
        float: left;
        margin-bottom: 10px;
        font-size: 14px;
        color: #969696;
    }
    .homepage .col-4 .cancel-info{
        color: #969696!important;
        font-size: 14px;
    }
    .homepage .col-4 .cancel-info:hover{
        color: #333!important;

    }
    .homepage .col-4 .function-btn {
        float: right;
        font-size: 13px;
        color: #969696 !important;
    }
    .homepage .col-4 .btn-hollow {
         font-size: 14px;
         text-align: center;
         width: 80px;
         color: #42c02e;
         border: 1px solid rgba(59,194,29,.7);
         color: #42c02e!important;
         border-radius: 15px;
        margin-right: 20px;
     }
    .homepage .col-4 .btn-hollow:hover {
        background: rgba(59,194,29,.2);

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
</style>