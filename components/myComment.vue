<template>
    <div>
        <div id="comment-list" class="comment-list">
            <!--提交的留言表单-->
            <form action="" class="new-comment">
                <nuxt-link to="/u/123" class="avatar">
                    <img src="../assets/img/default-avatar.jpg" alt="">
                </nuxt-link>
                <textarea  placeholder="写下你的评论" v-model="value" @focus="send = true"></textarea>
                <transition :duration="200" name="fade">
                    <div class="weite-function-block clearfix" v-if="send">
                        <div class="emoji-modal-wrap">
                            <a class="emoji" @click="showEmoji=!showEmoji">
                                <i class="fa fa-smile-o"></i>
                            </a>
                            <transition :duration="200" name="fade">
                                <div class="emoji-modal arrow-up" v-if="showEmoji">
                                    <vue-emoji @select="selectEmoji">

                                    </vue-emoji>
                                </div>
                            </transition>
                        </div>
                        <div class="hint">
                            Ctrl + Enter发表
                        </div>
                        <a href="javascript:voit(0)" class="btn btn-send" @click="sendData">
                            发送
                        </a>
                        <a href="javascript:voit(0)" class="cancel" @click="send = false">
                            取消
                        </a>
                    </div>
                </transition>
            </form>
            <!--留言的列表-->
            <div class="normal-comment-list" id="normal-comment-list">
                <!--留言的排序-->
                <div class="top-title">
                    <span>25条评论</span>
                    <a class="author-only" href="javascript:void(0)">只看作者</a>
                    <div class="pull-right">
                        <a class="active" href="javascript:void(0)">按喜欢排序</a>
                        <a href="javascript:void(0)">按时间正序</a>
                        <a href="javascript:void(0)">按时间倒序</a>
                    </div>
                </div>
                <!--留言的正文-->
                <div class="comment-placeholder" style="display: none">
                    <div class="author">
                        <div class="avatar"></div>
                        <div class="info">
                            <div class="name"></div>
                            <div class="meta"></div>
                        </div>
                    </div>
                    <div class="title"></div>
                    <div class="title animated-delay"></div>
                    <div class="tool-group">
                        <i class="fa fa-thumbs-o-up"></i>
                        <div class="zan"></div>
                        <i class="fa fa-comment-o"></i>
                        <div class="zan"></div>
                    </div>
                </div>
                <div v-for="(comment,index) in comments" :id="'comment-' + comment.id" class="comment">
                    <!--回复-->
                    <div class="comment-content">
                        <div class="author">
                            <div class="v-tooltip" >
                                <nuxt-link to="/u/123" class="avatar" :id="'info' + index" variant="primary">
                                    <img :src="comment.user.avatar" alt="">
                                </nuxt-link>
                                <b-popover :show.sync="comment.showPopid"
                                           :target="'info' + index" placement="top"
                                           triggers="hover focus" >
                                    <div class="user-info-content">
                                        <div class="avatar">
                                            <img :src="comment.user.avatar" alt="">
                                        </div>
                                        <div class="user-info">
                                            <nuxt-link to="/u/123" class="name">
                                                {{comment.user.nick_name}}
                                                <p>暂无个人简介</p>
                                            </nuxt-link>
                                            <div class="meta">
                                                <ul>
                                                    <li>
                                                        <nuxt-link to="/p/123">
                                                            <i class="fa fa-bookmark-o"></i>
                                                            领悟
                                                        </nuxt-link>
                                                    </li>
                                                    <li>
                                                        <nuxt-link to="/p/123">
                                                            <i class="fa fa-bookmark-o"></i>
                                                            良辰美景
                                                        </nuxt-link>
                                                    </li>
                                                    <li>
                                                        <nuxt-link to="/p/123">
                                                            <i class="fa fa-bookmark-o"></i>
                                                            带我走
                                                        </nuxt-link>
                                                    </li>
                                                </ul>
                                            </div>
                                        </div>
                                        <div class="user-info-footer">
                                            <ul>
                                                <li>
                                                    <p>18</p>
                                                    <span>文章</span>
                                                </li>
                                                <li>
                                                    <p>25</p>
                                                    <span>关注</span>
                                                </li>
                                                <li>
                                                    <p>222</p>
                                                    <span>粉丝</span>
                                                </li>
                                            </ul>
                                            <a href="javascript:void(0)" class="more-share">
                                                发简信
                                            </a>
                                            <a class="btn" href="javascript:void(0)" >
                                                <i class="fa" ></i>
                                                <span>关注</span>
                                            </a>
                                        </div>
                                    </div>
                                </b-popover>
                            </div>
                            <div class="info">
                                <nuxt-link to="/u/123" class="name">
                                    {{comment.user.nick_name}}
                                </nuxt-link>
                                <div class="meta">
                                    <span>
                                        {{comment.floor}}楼·{{comment.create_at}}
                                    </span>
                                </div>
                            </div>
                        </div>
                        <div class="comment-wrap"></div>
                    </div>
                    <!--二级回复-->
                    <div class="sub-comment-list"></div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    import vueEmoji from '~/components/vueEmoji'
    export default {
        name: "myComment",
        data () {
            return {
                send:false,
                showEmoji:false,
                value:'',
                comments:[
                    {
                        id:19935725,
                        floor:2,
                        liked:true,
                        showPopid:false,
                        like_count:112,
                        note_id:23054027,
                        user_id:6780849,
                        user:{
                            avatar:"/default-avatar.jpg",
                            id:6780849,
                            is_author:false,
                            nick_name:'一字千语',
                            badge:null,

                        },
                        create_at:'2018-02-02T09:26:11',
                        children_count:3,
                        compiled_content:'天王盖地虎',
                        children:[
                            {
                                id:20116365,
                                user_id:2604707,
                                user:{
                                    id:2604707,
                                    nick_name:'乔沃德·达基巴'
                                },
                                parent_id:19935725,
                                create_at:'2018-02-02T10:52:22',
                                compiled_content:'小鸡炖蘑菇',
                            },
                            {
                                id:20116362,
                                user_id:2604722,
                                user:{
                                    id:2604722,
                                    nick_name:'魔法少女郭德纲'
                                },
                                parent_id:19935725,
                                create_at:'2018-02-02T10:55:22',
                                compiled_content:'清风吹杨柳',
                            },
                            {
                                id:20045063,
                                user_id:20045063,
                                user:{
                                    id:20045063,
                                    nick_name:'Buka'
                                },
                                parent_id:19935725,
                                create_at:'2018-02-02T10:56:22',
                                compiled_content:'敢问是段友',
                            }

                        ]
                    },
                    {
                        id:20047377,
                        floor:3,
                        showPopid:false,
                        liked:true,
                        like_count:112,
                        note_id:23054027,
                        user_id:6718972,
                        user:{
                            avatar:'/default-avatar.jpg',
                            id:6718972,
                            is_author:false,
                            nick_name:'nike',
                            badge:null,

                        },
                        create_at:'2018-02-03T09:28:11',
                        children_count:2,
                        compiled_content:'惟妙惟肖又幽默风趣😂',
                        children:[
                            {
                                id:20116365,
                                user_id:2604708,
                                user:{
                                    id:2604708,
                                    nick_name:'不爱吃鱼大脸猫'
                                },
                                parent_id:19935725,
                                create_at:'2018-02-02T10:52:22',
                                compiled_content:'么么哒',
                            },
                            {
                                id:20116366,
                                user_id:2604766,
                                user:{
                                    id:2604766,
                                    nick_name:'陈独秀'
                                },
                                parent_id:19935725,
                                create_at:'2018-02-02T10:58:22',
                                compiled_content:'陈独秀同学，请你坐下',
                            },
                            {
                                id:20045054,
                                user_id:20045212,
                                user:{
                                    id:20045212,
                                    nick_name:'李大钊'
                                },
                                parent_id:19935725,
                                create_at:'2018-02-02T10:58:22',
                                compiled_content:'哈哈哈哈哈哈哈',
                            }

                        ]
                    },
                    {
                        id:20100836,
                        floor:4,
                        showPopid:false,
                        liked:true,
                        likes_count:10,
                        note_id:23054027,
                        user_id:7839387,
                        user:{
                            avatar:'/default-avatar.jpg',
                            id:7839387,
                            is_author:false,
                            nick_name:'长亭外的夏小乔',
                            badge:null
                        },
                        create_at:'2018-01-29T22:00:29',
                        children_count:1,
                        complied_content:'抢到沙发啦。',
                        children:[
                            {
                                id: 20100917,
                                user_id:8179167,
                                complied_content:'<a href="/users/22d2f8f31588" class="maleskine-author" target="_blank" data-user-slug="22d2f8f31588">@长亭外的夏小乔</a> ',
                                user:{
                                    id: 8179167,
                                    nickname: "渴死之水"
                                },
                                parent_id: 20100836,
                                created_at: "2018-01-29T22:02:13.000+08:00",
                            },
                            {
                                id: 20103918,
                                user_id:7839387,
                                complied_content:'<a href="/users/0371efd5f978" class="maleskine-author" target="_blank" data-user-slug="0371efd5f978">@渴死之水</a> 晚安，朋友，做个好梦。',
                                user:{
                                    id: 7839387,
                                    nickname: "长亭外的夏小乔"
                                },
                                parent_id: 20100836,
                                created_at: "2018-01-29T23:11:40.000+08:00",
                            },
                            {
                                id: 20104201,
                                user_id:8179167,
                                complied_content:'<a href="/users/22d2f8f31588" class="maleskine-author" target="_blank" data-user-slug="22d2f8f31588">@长亭外的夏小乔</a> ',
                                user:{
                                    id: 8179167,
                                    nickname: "渴死之水"
                                },
                                parent_id: 20100836,
                                created_at: "2018-01-29T23:19:55",
                            },
                        ]
                    },
                    {
                        id:20100123,
                        floor:5,
                        showPopid:false,
                        liked:true,
                        likes_count:0,
                        note_id:23054027,
                        user_id:7839311,
                        user:{
                            avatar:'/default-avatar.jpg',
                            id:7839311,
                            is_author:false,
                            nick_name:'乔沃德·达基巴',
                            badge:null
                        },
                        create_at:'2018-01-29T22:00:29',
                        children_count:1,
                        complied_content:'抢到沙发啦。'
                    }
                ]
            }
        },
        methods:{
          selectEmoji:function(code){
              this.showEmoji = false;
              this.value += code;
          },
          sendData:function(){
              console.log("发送信息")
          }
        },
        components:{
            vueEmoji
        }
    }
</script>

<style scoped>
    .fade-enter-active,.fade-leave-active {
        opacity: 1;
        transition: .3s;
        -webkit-transition: .3s
    }
    .fade-enter,.fade-leave-to {
        opacity: 0;
        transform: translate3d(0,-5%,0);
        -webkit-transform: translate3d(0,-5%,0);
        transition: .3s;
        -webkit-transition: .3s
    }
    .note .post .comment-list {
        padding-top: 20px;
    }
    .note .post .comment-list .new-comment{
        position: relative;
        margin-left: 48px;
        margin-bottom: 20px;

    }
    .note .post .comment-list .avatar{
        width: 38px;
        height: 38px;
        display: inline-block;
        margin-right: 5px;
    }
    .note .post .comment-list .new-comment .avatar{
        position: absolute;
        left: -48px;
    }
    .note .post .comment-list .new-comment textarea{
        width: 100%;
        height: 80px;
        padding: 10px 15px;
        border: 1px solid #ccc;
        border-radius: 4px;
        display: inline-block;
        vertical-align: top;
        outline-style: none;
        resize: none;
    }
    .note .post .comment-list .new-comment .emoji-modal-wrap{
        position: relative;

    }
    .note .post .comment-list .new-comment .emoji{
        float: left;
        margin-top: 18px;
    }
    .note .post .comment-list .new-comment .emoji i{
        font-size: 25px;
        color: #969696;
        cursor: pointer;
    }
    .note .post .comment-list .new-comment .emoji i:hover{
        color: #333;
    }
    .note .post .comment-list .new-comment .hint{
        float: left;
        margin: 20px 0 0 20px;
        font-size: 13px;
        color: #969696;
    }
    .note .post .comment-list .new-comment .cancel{
        float: right;
        font-size: 16px;
        margin: 20px 30px 0 0;
        color: #969696!important;
    }
    .note .post .comment-list .new-comment .cancel:hover{
        color: #333333!important;
    }
    .note .post .comment-list .new-comment .btn-send{
        float: right;
        width: 78px;
        padding: 8px 18px;
        margin: 10px 0;
        font-size: 16px;
        background: #42c02e;
        border-radius: 40px;
        color: white!important;
        text-align: center;
        box-shadow: none;
    }
    .note .post .comment-list .new-comment .btn-send:hover{
        background: #3db922;
    }
    .note .post .comment-list .new-comment .emoji-modal-wrap .emoji-modal {
        position: absolute;
        top: 50px;
        left: -48px;
        width: 402px;
        height: 208px;
        padding: 10px;
        border: 1px solid #d9d9d9;
        border-radius: 4px;
        box-shadow: 0 5px 20px rgba(0,0,0,.1);
        z-index: 999999;
        background: white;
    }
    .arrow-up:after{
        content: "";
        display: inline-block;
        position: absolute;
        left: 52px;
        top: -1px;
        width: 10px;
        height: 10px;
        border-left: 1px solid #d9d9d9;
        border-top: 1px solid #d9d9d9;
        transform: translate3d(0,-50%,0) rotate(-135deg);
        -webkit-transform: translate3d(0,-50%,0) rotate(45deg);
        background: white;
    }
    .note .post .comment-list .normal-comment-list {
        margin-top: 30px;
    }
    .note .post .comment-list .normal-comment-list .top-title{
        padding-bottom: 20px;
        border-bottom: 1px solid #f0f0f0;
    }
    .note .post .comment-list .normal-comment-list .top-title span{
        font-size: 17px;
        font-weight: 700;
    }
    .note .post .comment-list .normal-comment-list .top-title .author-only{
        font-size: 12px;
        padding: 4px 12px;
        border: 1px solid #e1e1e1;
        border-radius: 15px;
        color: #969696!important;
        margin-left: 10px;
    }
    .note .post .comment-list .normal-comment-list .top-title .pull-right a{
        margin-left: 10px;
        font-size: 12px;
        color: #969696!important;
    }
    .note .post .comment-list .normal-comment-list .top-title .pull-right a.active{
        color: #2f2f2f!important;
    }
    .note .post .comment-list .comment{
        padding: 20px 0 30px 0;
        /*border:1px solid #f0f0f0;*/
    }
    .note .post .comment-list .info{
        display: inline-block;
        margin-left: 10px;

    }
    .note .post .comment-list .info .name{
        font-size: 14px;
    }
    .note .post .comment-list .info .meta{
        font-size: 12px;
        color: #969696;
    }
    .note .post .comment-list .v-tooltip{
        display: inline-block;
    }
    .popover {
        max-width: 500px;
    }
    .popover .popover-body{
        padding: 0;
    }
    .popover .popover-body .user-info-content{
        width: 400px;

    }
    .popover .popover-body .user-info-content .avatar{
        width: 50px;
        height: 50px;
        float: left;
        margin: 0 8px;
    }
    .popover .popover-body .user-info-content .user-info{
        display: inline-block;
        margin-left: 40px;
        padding: 0px 50px 20px 10px;

    }
    .popover .popover-body .user-info-content .user-info>a{
          font-size: 16px;
          font-weight: 700;
    }
    .popover .popover-body .user-info-content .user-info>a p{
        color: #969696;
        font-size: 13px;
    }
    .popover .popover-body .user-info-content .user-info li{
        color: #969696;
        font-size: 12px;
        padding: 5px 0;
    }
    .popover .popover-body .user-info-content .user-info-footer{
        width: 400px;
        /*height: 60px;*/
        padding: 0;
        margin: 0;
        border-top: 1px solid #969696;
    }
    .popover .popover-body .user-info-content .user-info-footer ul{
        display: flex;
        text-align: center;
    }
    .popover .popover-body .user-info-content .user-info-footer ul li{
        padding: 5px 15px;
    }
    .popover .popover-body .user-info-content .user-info-footer ul li p{
        font-weight: 700;
        font-size: 18px;
        margin-bottom: 0;
     }
    .popover .popover-body .user-info-content .user-info-footer ul li span{
        color: #969696;
    }

</style>