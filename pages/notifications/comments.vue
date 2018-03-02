<template>
    <div>
        <my-header></my-header>
        <div class="my-container" style="padding:100px 15px">
            <div class="row">
                <div class="col-4">
                    <noti-count :data="notificationCount"></noti-count>
                </div>
                <div class="col-8 main">
                    <noti-conent style="display: none"></noti-conent>
                    <div class="menu">
                        收到的评论
                    </div>
                    <ul class="comment-list" @mouseover="showReport = true" @mouseleave="showReport = false">
                        <li class="">
                            <a href="/u/123" class="avatar">
                                <img src="~assets/img/movie.jpg">
                            </a>
                            <div class="info">
                                <div>
                                    <a class="user" href="/u/123">Nydia</a>
                                    <span class="comment-slogan">评论了你的文章</span>
                                    <a href="/p/123">《nihao》</a>
                                </div>
                                <div class="time">2018.03.02 13:50</div>
                            </div>
                            <p>你真的太厉害了 膜拜膜拜</p>
                            <div class="meta">
                                <a href="javascript:void(0)" class="function-btn" @click="showComment = !showComment; emojiFocus = !emojiFocus" >
                                    <i class="fa fa-comment-o"></i>
                                    <span>回复</span>
                                </a>
                                <a href="/p/123" class="function-btn">
                                    <i class="fa fa-mail-forward"></i><span>查看对话</span>
                                </a>
                                <a class="report" v-if="showReport">
                                    <span>举报</span>
                                </a>
                            </div>
                            <transition :duration="300" name="fade">
                                <form class="second-comment" v-if="showComment">
                                    <textarea v-model="value" v-focus="emojiFocus"></textarea>
                                    <div class="weite-function-block clearfix">
                                        <div class="emoji-modal-wrap">
                                            <a class="emoji" @click="showEmoji = !showEmoji">
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
                                        <a href="javascript:void(0)" class="btn btn-send" @click="sendComment">
                                            发送
                                        </a>
                                        <a href="javascript:void(0)" class="cancel" @click="closeComment">
                                            取消
                                        </a>
                                    </div>
                                </form>
                            </transition>
                        </li>
                    </ul>
                </div>
            </div>

        </div>
    </div>

</template>

<script>
  import myHeader from '../../components/myHeader'
  import notiCount from '../../components/notificationsLeft'
  import notiConent from '../../components/notiComment'
  import vueEmoji from '../../components/vueEmoji'
  export default {
    name: 'comments',
    components:{
      myHeader,
      notiCount,
      notiConent,
        vueEmoji,
    },
    data(){
      return{
          notificationCount:0,
          showReport:false,
          showEmoji:false,
          emojiFocus:false,
          value:'@Nydia',
          showComment:false
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
              this.value = '@Nydia';
              this.sendCommentBtn = false;
              this.emojiFocus = false;
              this.showComment = false;
          },
          closeComment:function(){
              this.value = '@Nydia';
              this.sendCommentBtn = false;
              this.emojiFocus = false;
              this.showComment = false;
          },
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
     .main .menu {
        margin-bottom: 20px;
        font-size: 14px;
        font-weight: 700;
    }

    .main .comment-list li{
        padding: 20px 0;
        border-top: 1px solid #f0f0f0;
    }
     .main .comment-list .avatar{
         display: inline-block;
         margin-right: 5px;
         width: 40px;
         height: 40px;
     }
     .main .comment-list .info {
         display: inline-block;
         vertical-align: top;
         width: 535px;
         font-size: 15px;
         line-height: 1.7;
     }
     .main .comment-list .info .user{
         color: #333333!important;
     }
    .main .comment-list .info a{
        color: #3194d0!important;
    }
    .main .comment-list .info .time{
        font-size: 12px;
        color: #969696;
    }
    .main .comment-list p{
        margin: 10px 0 0;
        font-size: 15px;
        line-height: 1.7;
    }
     .main .comment-list .meta .function-btn{
         float: left;
         margin-right: 30px;
         font-size: 13px;
         color: #969696!important;
         margin-top: 10px;
     }
    .main .comment-list .meta .report{
        float: right;
        font-size: 13px;
        color: #969696!important;
        cursor: pointer;
    }
     .main .comment-list .meta .report:hover{
         color: #333333!important;
         cursor: pointer;
     }
     .main .comment-list .second-comment{
         position: relative;
         margin-top: 40px;
     }
     .main .comment-list .second-comment textarea{
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
     .main .comment-list .second-comment .emoji-modal-wrap{
         position: relative;

     }
     .main .comment-list .second-comment .emoji{
         float: left;
         margin-top: 18px;
     }
     .main .comment-list .second-comment .emoji i{
         font-size: 25px;
         color: #969696;
         cursor: pointer;
     }
     .main .comment-list .second-comment .emoji i:hover{
         color: #333;
     }
     .main .comment-list .second-comment .hint{
         float: left;
         margin: 20px 0 0 20px;
         font-size: 13px;
         color: #969696;
     }
     .main .comment-list .second-comment .cancel{
         float: right;
         font-size: 16px;
         margin: 20px 30px 0 0;
         color: #969696!important;
     }
     .main .comment-list .second-comment .cancel:hover{
         color: #333333!important;
     }
     .main .comment-list .second-comment .btn-send{
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
     .main .comment-list .second-comment .btn-send:hover{
         background: #3db922;
     }
     .main .comment-list .second-comment .emoji-modal-wrap .emoji-modal {
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
</style>