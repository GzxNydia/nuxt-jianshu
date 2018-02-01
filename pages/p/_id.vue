<template>
    <div>
        <my-header></my-header>
        <div class="note" @click="moreClick = false">
            <!--文章区域-->
            <div class="post">
                <!--正文-->
                <div class="article">
                    <h1 class="title">
                        爱，就是一起吃好多好多顿饭
                    </h1>
                    <div class="author">
                        <nuxt-link to="/u/123" class="avatar">
                            <img src="../../assets/img/default-avatar.jpg" alt="">
                        </nuxt-link>
                        <div class="info">
                            <span class="name">测试用户</span>
                            <a class="btn-sm" href="javascript:void(0)" :class="followObj" @click="isFollow" @mouseover="noFollow" @mouseleave="beFollow">
                                <i class="fa" :class="iconObj" ref="icon"></i>
                                <span ref="followWord">关注</span>
                            </a>
                            <div class="meta">
                                <span>2018.01.23 16:00</span>
                                <span>字数 2273</span>
                                <span>阅读 222</span>
                                <span>评论 123</span>
                                <span>喜欢 55</span>
                            </div>
                        </div>
                    </div>
                    <div class="show-content">
                        <p>美食和爱情很像，一个惊动味蕾，一个触动感官。你会记得美味入口的那一瞬间，你也忘不了初次相见的那个人。</p>
                        <p>最初的惊艳感仍在，等之后熟悉了，会渐渐化成恬淡的温情。味蕾想念某样食物，心里牵挂一个人。知道他们一直都在，才会心生安定。</p><p>食物和爱，是怎么也脱不开关系的。厨房间的事一向琐碎，下厨的动力，无非是爱吧。亲人、爱人、好友，挨着坐的亲密，举杯一饮而快，或只是闲聊碎语，多少故事在此间发生。</p><p>今天想聊一聊日本女作家向田邦子。在她的散文、小说和书信中，常常提到各式食物，而展开来，说到底，与之相关的，还是人间的种种情感。她爱美食，“我靠写字赚钱已有二十年，但比起拿笔的时间，拿筷子的时间肯定更长。”担当编剧，敏锐观察日常的她，记录下来的这些食物故事，是有温度的，带着她独有的柔情笔触。</p><p><b>1 童年的回忆</b></p><p>不全是出奇的记忆力，也许是浸润在一个于细微小事上流淌爱意的家庭氛围里，向田邦子总能活灵活现地描绘出画面感，小孩子的馋嘴，大人的宠溺，有趣又有甜意。</p>
                        <p>小时候常在半夜被叫起床。</p>
                        <p>因为父亲参加晚宴夜归，带了剩菜回来。由于当时的小妹还是婴儿，所以总是由我带头，三姐弟穿着睡衣、身上披件毛衣或铺棉外挂来到客厅。</p>
                        <p>有时他也会讨好长女的我，“上次是保雄先选的，今天晚上该轮到邦子了。”并用小碟子帮我们分配食物。</p>
                        <p>连头带尾巴的鲷鱼放在盘中央，周围排列着鱼板、甜糕、干烧明虾，甚至还有绿色的羊羹。我虽然受不了父亲一身的酒臭味，但是平常爱骂人的他像变了一个人似的招呼“我们”快吃，而且又能将爱吃的东西一个个往嘴里送，感觉还真不错。</p>
                        <p>只不过我们实在是太困了，尤其是素有“睡觉大王”之称的弟弟竟然是闭着眼，光嘴巴在动。我还记得被祖母抱在怀里的弟弟手上依然紧紧抓着筷子，害得母亲得用力一根一根地扳开他的手指才拿得出来。</p>
                        <p>其实最想睡的人应该是父亲，他常常靠在餐桌上或枕在手臂上看着孩子们的吃相，不到十五或二十分钟便醉意泛起，发出如雷的鼾声睡着了。</p>
                        <p>……</p>
                    </div>
                    <div class="show-foot">
                        <nuxt-link to="/nb/123" class="notebook">
                            <i class="fa fa-book"></i>
                            <span>我的文集</span>
                        </nuxt-link>
                        <div class="copyright">
                            © 著作权归作者所有
                        </div>
                    </div>
                    <div class="follow-detail">
                        <div class="info">
                            <nuxt-link to="/u/123" class="avatar">
                                <img src="../../assets/img/default-avatar.jpg" alt="">
                            </nuxt-link>
                            <a class="btn" href="javascript:void(0)" :class="followObj" @click="isFollow" @mouseover="noFollow" @mouseleave="beFollow">
                                <i class="fa" :class="iconObj" ref="icon2"></i>
                                <span ref="followWord2">关注</span>
                            </a>
                            <nuxt-link to="/u/123" class="name">
                                测试用户
                            </nuxt-link>
                            <i class="fa fa-mars"></i>
                            <div class="meta">
                                <span>2018.01.23 16:00</span>
                                <span>字数 2273</span>
                                <span>阅读 222</span>
                                <span>评论 123</span>
                                <span>喜欢 55</span>
                            </div>
                        </div>
                        <div class="signature">
                            这个人很懒，什么都没留下。
                        </div>
                    </div>
                    <div class="meta-bottom">
                        <div class="like">
                            <div class="btn like-group" ref="bgShow">
                                <div class="btn-like">
                                    <a href="javascript:void(0)"  @click="isLike">
                                        <i class="fa fa-heart-o"></i>
                                        <span>喜欢</span>
                                    </a>
                                </div>
                                <div class="modal-wrap">
                                    <a href="javascript:void(0)">{{likeCount}}</a>
                                </div>
                            </div>

                        </div>
                        <div class="share-group">
                            <a href="javascript:void(0)"  v-b-tooltip.hover  title ="分享到微博"
                            >
                                <i class="fa fa-weibo weibo"></i>
                            </a>
                            <a href="javascript:void(0)" v-b-tooltip.hover  title ="分享到微信">
                                <i class="fa fa-weixin weixin"></i>
                            </a>
                            <a href="javascript:void(0)" v-b-tooltip.hover  title ="下载长微博图片">
                                <i class="fa fa-picture-o pic"></i>
                            </a>
                            <a href="javascript:void(0)" class="more-share" @click.stop="moreClick = true">
                                更多分享
                            </a>
                            <div class="share-model" v-if="moreClick">
                                <ul>
                                    <li>
                                        <a href="javascript:void (0)">
                                            <i class="fa fa-quora qq"></i>
                                            分享到QQ空间
                                        </a>
                                    </li>
                                    <li>
                                        <a href="javascript:void (0)">
                                            <i class="fa fa-twitter tw"></i>
                                            分享到Twitter
                                        </a>
                                    </li>
                                    <li>
                                        <a href="javascript:void (0)">
                                            <i class="fa fa-facebook-official face"></i>
                                            分享到Facebook
                                        </a>
                                    </li>
                                    <li>
                                        <a href="javascript:void (0)">
                                            <i class="fa fa-google-plus go"></i>
                                            分享到Google+
                                        </a>
                                    </li>
                                    <li>
                                        <a href="javascript:void (0)">
                                            <i class="fa dou">豆</i>
                                            分享到豆瓣
                                        </a>
                                    </li>
                                </ul>
                                <div class="san"></div>
                            </div>
                        </div>

                    </div>
                </div>
                <!--回复组件-->
                <my-comment></my-comment>
            </div>
            <!--悬浮操作框-->
            <div class="side-bar"></div>
            <!--对应的推荐阅读-->
            <div class="note-bottom"></div>
        </div>
    </div>
</template>

<script>
    import myHeader from '~/components/myHeader'
    import myComment from '~/components/myComment'
    export default {
        name: "ID",
        components:{
            myHeader,
            myComment
        },
        data(){
            return {
                followObj:{
                    'follow':true,
                    'following':false
                },
                iconObj:{
                    'fa-plus-square-o':true,
                    'fa-check':false
                },
                likeCount:120,
                moreClick:false
            }
        },
        methods:{
            isFollow:function(){
                this.followObj.follow = !this.followObj.follow;
                this.followObj.following = !this.followObj.following;
                this.iconObj['fa-plus-square-o'] = !this.iconObj['fa-plus-square-o'];
                this.iconObj['fa-check'] = !this.iconObj['fa-check'];
                let word = this.$refs.followWord.innerHTML;
                this.$refs.followWord.innerHTML = word == '关注' ? '已关注' : '关注';
                this.$refs.followWord2.innerHTML = word == '关注' ? '已关注' : '关注';
            },
            noFollow:function(){
                let word = this.$refs.followWord.innerHTML;
                if(word == '已关注'){
                    this.$refs.followWord.innerHTML = '取消关注';
                    this.$refs.icon.className = 'fa fa-close';
                    this.$refs.followWord2.innerHTML = '取消关注';
                    this.$refs.icon2.className = 'fa fa-close';
                }
            },
            beFollow:function(){
                let word = this.$refs.followWord.innerHTML;
                if(word == '取消关注'){
                    this.$refs.followWord.innerHTML = '已关注';
                    this.$refs.icon.className = 'fa fa-check';
                    this.$refs.followWord2.innerHTML = '已关注';
                    this.$refs.icon2.className = 'fa fa-check';
                }
            },
            isLike:function(){
                if(!this.$refs.bgShow.classList.contains('active')){
                    this.$refs.bgShow.classList.add('active');
                    this.likeCount = this.likeCount+1
                }else{
                    this.$refs.bgShow.classList.remove('active');
                    this.likeCount = this.likeCount-1
                }

            }
        }
    }
</script>

<style scoped>

</style>