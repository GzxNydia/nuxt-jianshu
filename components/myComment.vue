<template>
    <div>
        <div id="comment-list" class="comment-list">
            <!--提交的留言表单-->
            <form action="" class="new-comment">
                <nuxt-link to="/u/123" class="avatar">
                    <img src="../assets/img/default-avatar.jpg" alt="">
                </nuxt-link>
                <textarea  placeholder="写下你的评论" @focus="send_one = true"></textarea>
                <transition :duration="200" name="fade">
                    <div class="weite-function-block clearfix" v-if="send_one">
                        <div class="emoji-modal-wrap">
                            <a class="emoji" @click="showEmoji=!showEmoji">
                                <i class="fa fa-smile-o"></i>
                            </a>
                            <transition :duration="200" name="fade">
                                <div class="emoji-modal arrow-up" v-if="showEmoji">

                                </div>
                            </transition>

                        </div>
                        <div class="hint">
                            Ctrl + Enter发表
                        </div>
                        <a href="javascript:voit(0)" class="btn btn-send">
                            发送
                        </a>
                        <a href="javascript:voit(0)" class="cancel" @click="send_one = false">
                            取消
                        </a>
                    </div>
                </transition>

            </form>
        </div>
    </div>
</template>

<script>
    export default {
        name: "myComment",
        data () {
            return {
                send_one:false,
                showEmoji:false
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
        margin-bottom: 500px;
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
        width: 360px;
        height: 200px;
        border: 1px solid #d9d9d9;
        border-radius: 4px;
        box-shadow: 0 5px 20px rgba(0,0,0,.1);
        z-index: 999999;
    }
    .arrow-up:after{
        content: "";
        position: absolute;
        left: 52px;
        width: 10px;
        height: 10px;
        border-left: 1px solid #d9d9d9;
        border-top: 1px solid #d9d9d9;
        transform: translate3d(0,-50%,0) rotate(-135deg);
        -webkit-transform: translate3d(0,-50%,0) rotate(45deg);
        background: white;

    }
</style>