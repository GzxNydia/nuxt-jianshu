<template>
    <div>
        <div id="comment-list" class="comment-list">
            <!--提交的留言表单-->
            <form action="" class="new-comment">
                <nuxt-link to="/u/123" class="avatar">
                    <img src="../assets/img/default-avatar.jpg" alt="">
                </nuxt-link>
                <textarea v-focus="emojiFocus" @focus="sendCommentBtn=true" placeholder="写下你的评论" v-model="value"></textarea>
                <transition :duration="200" name="fade">
                    <div v-if="sendCommentBtn" class="write-function-block clearfix">
                        <div class="emoji-modal-wrap">
                            <a href="javascript:void(0)" @click="showEmoji=!showEmoji" class="emoji">
                                <i class="fa fa-smile-o"></i>
                            </a>
                            <transition :duration="200" name="fade">
                                <div v-if="showEmoji" class="emoji-modal arrow-up">
                                    <vue-emoji @select="selectEmoji"></vue-emoji>
                                </div>
                            </transition>
                        </div>
                        <div class="hint">
                            Ctrl+Enter 发表
                        </div>
                        <a class="btn btn-send" href="javascript:void(0)" @click="sendComment">发送</a>
                        <a class="cancel" href="javascript:void(0)" @click="closeComment">取消</a>
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
                                        {{comment.floor}}楼·{{comment.create_at|formatDate}}
                                    </span>
                                </div>
                            </div>
                        </div>
                        <div class="comment-wrap">
                            <p v-html="comment.compiled_content"></p>
                            <div class="tool-group">
                                <a href="javascript:void(0)" @click="isZan(index)" class="zan like-bottom zan-animation">
                                    <i class="fa" :class="comment.liked ? 'fa-thumbs-up liked' : 'fa-thumbs-o-up'"></i>
                                    <span :class="comment.liked ? 'real-like':''">{{comment.like_count}}人点赞</span>
                                </a>
                                <a href="javascript:void(0)" @click="showSubCommentForm(index,'top','')">
                                    <i class="fa fa-comment-o"></i>
                                    <span>回复</span>
                                </a>

                            </div>
                        </div>
                    </div>
                    <!--二级回复-->
                    <div class="sub-comment-list">
                        <div v-show="comment.children.length != 0" v-for="(subComment,nindex) in comment.children" :keys="nindex" :id="'comment' + subComment.id" class="sub-comment">
                            <p>
                                <nuxt-link to="/u/123">
                                    {{subComment.user.nick_name}}
                                </nuxt-link>
                                :
                                <span v-html="subComment.compiled_content"></span>
                            </p>
                            <div class="sub-tool-group">
                                <span>{{subComment.create_at|formatDate}}</span>
                                <a href="javascript:void(0)" @click="showSubCommentForm(index,subComment.id,subComment.user.nick_name)">
                                    <i class="fa fa-comment-o"></i>
                                    <span>回复</span>
                                </a>
                            </div>
                        </div>
                        <div v-show="comment.children.length != 0" class="more-comment">
                            <a href="javascript:void(0)" @click="showSubCommentForm(index,'bottom','')" class="add-comment-btn">
                                <i class="fa fa-pencil"></i>
                                <span>添加新评论</span>
                            </a>
                        </div>
                        <transition :duration="300" name="fade">
                            <form class="second-comment" v-if="activeIndex.includes(index)">
                            <textarea v-model="subCommentList[index]" placeholder="写下你的评论" v-focus="commentFormState[index]" @blur="commentFormState[index]=false"></textarea>
                                <div class="weite-function-block clearfix">
                                    <div class="emoji-modal-wrap">
                                        <a class="emoji" @click="showSubEmoji(index)">
                                            <i class="fa fa-smile-o"></i>
                                        </a>
                                        <transition :duration="200" name="fade">
                                            <div class="emoji-modal arrow-up" v-if="emojiIndex.includes(index)">
                                                <vue-emoji @select="selectSubEmoji">

                                                </vue-emoji>
                                            </div>
                                        </transition>
                                    </div>
                                    <div class="hint">
                                        Ctrl + Enter发表
                                    </div>
                                    <a href="javascript:void(0)" class="btn btn-send" @click="sendSubCommentData(index)">
                                        发送
                                    </a>
                                    <a href="javascript:void(0)" class="cancel" @click="closeSubComment(index)">
                                        取消
                                    </a>
                                </div>
                        </form>
                        </transition>
                    </div>
                    <!--显示表单-->
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    import Vue from 'vue'
    import vueEmoji from '~/components/vueEmoji'
    export default {
        name: "myComment",
        data () {
            return {
                sendCommentBtn:false,
                showEmoji:false,
                value:'',
                emojiFocus:false,
                activeIndex:[],
                emojiIndex:[],
                comments:[
                    {
                        id:19935725,
                        floor:2,
                        liked:true,
                        showPopid:false,
                        like_count:100,
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
                        like_count:10,
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
                        compiled_content:'抢到沙发啦 <br> 哈哈哈哈哈哈哈哈',
                        children:[
                            {
                                id: 20100917,
                                user_id:8179167,
                                compiled_content:'@长亭外的夏小乔 略略略',
                                user:{
                                    id: 8179167,
                                    nick_name: "渴死之水"
                                },
                                parent_id: 20100836,
                                create_at:'2018-02-02T10:52:22',
                            },
                            {
                                id: 20103918,
                                user_id:7839387,
                                compiled_content:' 晚安，<br>朋友，做个好梦。',
                                user:{
                                    id: 7839387,
                                    nick_name: "长亭外的夏小乔"
                                },
                                parent_id: 20100836,
                                create_at:'2018-02-02T10:52:22',
                            },
                            {
                                id: 20104201,
                                user_id:8179167,
                                compiled_content:'❤❤❤❤❤',
                                user:{
                                    id: 8179167,
                                    nick_name: "渴死之水"
                                },
                                parent_id: 20100836,
                                create_at:'2018-02-02T10:52:22',
                            },
                        ]
                    },
                    {
                        id:20100123,
                        floor:5,
                        showPopid:false,
                        liked:false,
                        like_count:0,
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
                        compiled_content:'厉害了 哈哈哈哈哈哈哈哈哈<br>笑的我大姨妈都漏了，你赔 666666666666666666666666666',
                        children:[]
                    }
                ],
                subCommentList:[],
                commentFormState:[],
                commentId:[],
            }
        },
        methods:{
            selectEmoji:function(code){
              this.showEmoji = false;
              this.value += code;
              this.emojiFocus = true;
            },
            sendComment:function(){
                  console.log("发送信息");
                  this.value = '';
                  this.sendCommentBtn = false;
                  this.emojiFocus = false;
            },
            closeComment:function(){
                this.value = '';
                this.sendCommentBtn = false;
                this.emojiFocus = false;
            },
            isZan:function(index){
                if(this.comments[index].liked){
                    //点赞过后再点就是取消点赞
                    this.comments[index].liked = false;
                    --this.comments[index].like_count
                    //留下取消点赞的ajax
                }else{
                    //没有点赞再点就是点赞
                    this.comments[index].liked = true;
                    ++this.comments[index].like_count
                    //留下添加点赞的请求
                }
            },
            showSubCommentForm:function(index,id,name){
                let ID = id.toString();
                if(this.commentId[index] == ID){
                    //点两次
                    this.activeIndex.splice(this.activeIndex.indexOf(index),1);
                    this.commentId[index] = '';
                }else{
                    //点一次
                    //清除表单内容
                    this.subCommentList[index] = '';
                    //表情关掉
                    this.emojiIndex = [];
                    if(!this.activeIndex.includes(index)){
                        this.activeIndex.push(index);
                    }
                    // 判断用户名是否存在，如果存在添加
                    if(name != ''){
                        this.subCommentList[index] = `@${name} `;
                    }
                    //存一下上一个回复列表对应点击的按钮
                    this.commentId[index] = ID;
                    //获取焦点
                    this.commentFormState[index] = true;
                }
            },
            sendSubCommentData:function(value){
                let index = this.activeIndex.indexOf(value);
                this.activeIndex.splice(index,1);
                //value是下标
                console.log(this.subCommentList[value])
                this.commentId[value] = '';
            },
            closeSubComment:function(value){
                let index = this.activeIndex.indexOf(value);
                this.activeIndex.splice(index,1);
                this.commentId[value] = '';

            },
            showSubEmoji:function(value){
                if(this.emojiIndex.includes(value)){
                    let index = this.emojiIndex.indexOf(value);
                    this.emojiIndex.splice(index,1);
                }else{
                    this.emojiIndex.push(value);
                }

            },
            selectSubEmoji:function(code){
                //当前下标
                let index = this.emojiIndex[0];
                //将表情所代表的code值放入表单当中.
                if(this.subCommentList[index] == null){
                    this.subCommentList[index] = '';
                }
                this.subCommentList[index] += code;
                //关掉emoji弹出框
                this.emojiIndex = [];
                //聚焦一下
                this.commentFormState[index] = true;
            },

        },
        components:{
            vueEmoji
        },
        directives: {
            // 除了默认设置的核心指令( v-model 和 v-show ),Vue 也允许注册自定义指令。
            // 对纯 DOM 元素进行底层操作
            // 注册局部指令，在模板中任何元素上使用新的 v-focus 属性
            "focus": {
                // 钩子函数：bind inserted update componentUpdated unbind
                // 钩子函数的参数：el，binding，vnode，oldVnode
                bind:function(el,{value}){
                    if(value){
                        el.focus();
                    }
                },
                update:function(el,{value}){
                    if(value){
                        el.focus();
                    }

                },
                inserted: function (el,{value}) {
                    if(value){
                        el.focus();
                    }
                }
            }
        },
        watch:{
            subCommentList:function(val){
                console.log(val);
            }
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
        padding: 5px 0;

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
    .note .post .comment-list .comment-content .author{
        margin-bottom: 15px;
    }
    .note .post .comment-list .comment p{
        font-size: 16px;
        margin: 10px 0;
        line-height: 1.5;
        word-break: break-all!important;
    }
    .note .post .comment-list .comment .tool-group a{
        color: #969696!important;
        margin-right: 10px;
    }
    .note .post .comment-list .comment .tool-group a:hover{
        color: #333333!important;
    }
    .note .post .comment-list .comment .tool-group a i{
         font-size: 18px;
         margin-right: 5px;
     }
    .note .post .comment-list .comment .tool-group .zan:hover i{
        color: #ea6f5a;
    }
    .note .post .comment-list .comment .tool-group .active i{
        color: #ea6f5a!important;
    }
    .note .post .comment-list .comment .tool-group i.liked {
        color: #ea6f5a;
    }
    .note .post .comment-list .comment .tool-group span.real-like {
        color: #333;
    }
    .note .post .comment-list .comment .tool-group .active span{
        color: #333333;
    }
    .note .post .comment-list .second-comment{
        position: relative;
        margin-top: 10px;
    }
    .note .post .comment-list .second-comment textarea{
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
    .note .post .comment-list .second-comment .emoji-modal-wrap{
        position: relative;

    }
    .note .post .comment-list .second-comment .emoji{
        float: left;
        margin-top: 18px;
    }
    .note .post .comment-list .second-comment .emoji i{
        font-size: 25px;
        color: #969696;
        cursor: pointer;
    }
    .note .post .comment-list .second-comment .emoji i:hover{
        color: #333;
    }
    .note .post .comment-list .second-comment .hint{
        float: left;
        margin: 20px 0 0 20px;
        font-size: 13px;
        color: #969696;
    }
    .note .post .comment-list .second-comment .cancel{
        float: right;
        font-size: 16px;
        margin: 20px 30px 0 0;
        color: #969696!important;
    }
    .note .post .comment-list .second-comment .cancel:hover{
        color: #333333!important;
    }
    .note .post .comment-list .second-comment .btn-send{
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
    .note .post .comment-list .second-comment .btn-send:hover{
        background: #3db922;
    }
    .note .post .comment-list .second-comment .emoji-modal-wrap .emoji-modal {
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
    .note .post .comment-list .comment .tool-group a span{
        font-size: 14px;

    }
    .note .post .comment-list .sub-comment-list{
        border-left: 2px solid #d9d9d9;
        margin-top: 10px;
        padding: 0 20px;
    }
    .note .post .comment-list .sub-comment{
        padding-bottom: 15px;
        margin-bottom: 15px;
        border-bottom: 1px dashed #f0f0f0;
    }
    .note .post .comment-list .sub-comment p{
        font-size: 14px;
        line-height: 1.5;
        margin-bottom: 5px;
    }
    .note .post .comment-list .sub-comment p a{
        color: #3194d0!important;
    }
    .note .post .comment-list .sub-tool-group{
        color: #969696;
        font-size: 12px;
    }
    .note .post .comment-list .sub-tool-group a{
             margin-left: 10px;
         }
    .note .post .comment-list .sub-tool-group a i{
        margin-right: 10px;
    }
    .note .post .comment-list .more-comment{
        font-size: 14px;
        color: #969696;
    }
    .note .post .comment-list .more-comment i{
        margin-right: 5px;
    }
    .note .post .comment-list .more-comment a:hover{
        color: #333333!important;
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