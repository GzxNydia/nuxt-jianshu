<template>
    <div>
        <my-header></my-header>
        <div class="index my-container">
            <div class="row">
                <div class="col-8 main">
                    <div v-swiper:mySwiper="swiperOption" class="banner">
                        <div class="swiper-wrapper">
                            <div class="swiper-slide" v-for="banner in banners">
                                <img :src="banner">
                            </div>
                        </div>
                        <div class="swiper-pagination swiper-pagination-white"></div>
                        <div class="swiper-button-prev swiper-button-white"></div>
                        <div class="swiper-button-next swiper-button-white"></div>
                    </div>
                    <!--推荐专题-->
                    <div class="recommend-collection">
                        <nuxt-link to="/collection/123">
                            <img src="../assets/img/1.jpg" alt="">
                            <span>文学</span>
                        </nuxt-link>
                        <nuxt-link to="/collection/123">
                            <img src="../assets/img/2.jpg" alt="">
                            <span>摄影</span>
                        </nuxt-link>
                        <nuxt-link to="/collection/123">
                            <img src="../assets/img/3.jpg" alt="">
                            <span>@IT互联网</span>
                        </nuxt-link>
                        <nuxt-link to="/collection/123">
                            <img src="../assets/img/1.jpg" alt="">
                            <span>文学</span>
                        </nuxt-link>
                        <nuxt-link to="/collection/123">
                            <img src="../assets/img/2.jpg" alt="">
                            <span>摄影</span>
                        </nuxt-link>
                        <nuxt-link to="/collection/123">
                            <img src="../assets/img/3.jpg" alt="">
                            <span>@IT互联网</span>
                        </nuxt-link>
                        <nuxt-link to="/collection/123">
                            <img src="../assets/img/2.jpg" alt="">
                            <span>摄影</span>
                        </nuxt-link>
                        <nuxt-link to="/collection/123">
                            <img src="../assets/img/3.jpg" alt="">
                            <span>@IT互联网</span>
                        </nuxt-link>
                        <nuxt-link to="/collection/123" class="more-hot-collection">
                            更多热门专题
                            <i class="fa fa-angle-right"></i>
                        </nuxt-link>
                    </div>
                    <div class="split-line"></div>
                    <!--文章列表-->
                    <div id="list-container">
                        <ul class="note-list">
                            <li class="have-img">
                                <nuxt-link to="/p/123" class="wrap-img">
                                    <img src="../assets/img/pic.jpg" alt="">
                                </nuxt-link>
                                <div class="content">
                                    <div class="author">
                                        <nuxt-link to="/u/123" class="avatar">
                                            <img src="../assets/img/default-avatar.jpg" alt="">
                                        </nuxt-link>
                                        <div class="info">
                                            <nuxt-link to="/u/123" class="nickname">
                                                测试用户
                                            </nuxt-link>
                                            <span class="time">8小时前</span>
                                        </div>
                                    </div>
                                    <nuxt-link to="/p/123" class="title">
                                        如何把知识转化为能力，这是我见过的最好的回答
                                    </nuxt-link>
                                    <p class="abstract">
                                        随着知识经济的兴起，读书的重要性得到了大家的普遍认同，于是市场上出现很多读书方法，比如速度、多读、慢读、列读……不管你采用哪一种读书方法，最终都要回归到“行动”二字上，正如陆...
                                    </p>
                                    <div class="meta">
                                        <nuxt-link to="/collecton/123"  class="collection-tag">
                                            短篇小说
                                        </nuxt-link>
                                        <nuxt-link to="/p/123" class="color-change">
                                            <i class="fa fa-eye"></i>
                                            555
                                        </nuxt-link>
                                        <nuxt-link to="/p/123" class="color-change">
                                            <i class="fa fa-comments"></i>
                                            555
                                        </nuxt-link>
                                        <span>
                                           <i class="fa fa-heart"></i>
                                           200
                                        </span>
                                    </div>
                                </div>
                            </li>
                            <li>
                                <div class="content">
                                    <div class="author">
                                        <nuxt-link to="/u/123" class="avatar">
                                            <img src="../assets/img/default-avatar.jpg" alt="">
                                        </nuxt-link>
                                        <div class="info">
                                            <nuxt-link to="/u/123" class="nickname">
                                                测试用户
                                            </nuxt-link>
                                            <span class="time">8小时前</span>
                                        </div>
                                    </div>
                                    <nuxt-link to="/p/123" class="title">
                                        如何把知识转化为能力，这是我见过的最好的回答
                                    </nuxt-link>
                                    <p class="abstract">
                                        随着知识经济的兴起，读书的重要性得到了大家的普遍认同，于是市场上出现很多读书方法，比如速度、多读、慢读、列读……不管你采用哪一种读书方法，最终都要回归到“行动”二字上，正如陆...
                                    </p>
                                    <div class="meta">
                                        <nuxt-link to="/collecton/123"  class="collection-tag">
                                            短篇小说
                                        </nuxt-link>
                                        <nuxt-link to="/p/123" class="color-change">
                                            <i class="fa fa-eye"></i>
                                            555
                                        </nuxt-link>
                                        <nuxt-link to="/p/123" class="color-change">
                                            <i class="fa fa-comments"></i>
                                            555
                                        </nuxt-link>
                                        <span>
                                           <i class="fa fa-heart"></i>
                                           200
                                        </span>
                                    </div>
                                </div>
                            </li>
                            <li class="have-img">
                                <nuxt-link to="/p/123" class="wrap-img">
                                    <img src="../assets/img/pic.jpg" alt="">
                                </nuxt-link>
                                <div class="content">
                                    <div class="author">
                                        <nuxt-link to="/u/123" class="avatar">
                                            <img src="../assets/img/default-avatar.jpg" alt="">
                                        </nuxt-link>
                                        <div class="info">
                                            <nuxt-link to="/u/123" class="nickname">
                                                测试用户
                                            </nuxt-link>
                                            <span class="time">8小时前</span>
                                        </div>
                                    </div>
                                    <nuxt-link to="/p/123" class="title">
                                        如何把知识转化为能力，这是我见过的最好的回答
                                    </nuxt-link>
                                    <p class="abstract">
                                        随着知识经济的兴起，读书的重要性得到了大家的普遍认同，于是市场上出现很多读书方法，比如速度、多读、慢读、列读……不管你采用哪一种读书方法，最终都要回归到“行动”二字上，正如陆...
                                    </p>
                                    <div class="meta">
                                        <nuxt-link to="/collecton/123"  class="collection-tag">
                                            短篇小说
                                        </nuxt-link>
                                        <nuxt-link to="/p/123" class="color-change">
                                            <i class="fa fa-eye"></i>
                                            555
                                        </nuxt-link>
                                        <nuxt-link to="/p/123" class="color-change">
                                            <i class="fa fa-comments"></i>
                                            555
                                        </nuxt-link>
                                        <span>
                                           <i class="fa fa-heart"></i>
                                           200
                                        </span>
                                    </div>
                                </div>
                            </li>
                            <li>
                                <div class="content">
                                    <div class="author">
                                        <nuxt-link to="/u/123" class="avatar">
                                            <img src="../assets/img/default-avatar.jpg" alt="">
                                        </nuxt-link>
                                        <div class="info">
                                            <nuxt-link to="/u/123" class="nickname">
                                                测试用户
                                            </nuxt-link>
                                            <span class="time">8小时前</span>
                                        </div>
                                    </div>
                                    <nuxt-link to="/p/123" class="title">
                                        如何把知识转化为能力，这是我见过的最好的回答
                                    </nuxt-link>
                                    <p class="abstract">
                                        随着知识经济的兴起，读书的重要性得到了大家的普遍认同，于是市场上出现很多读书方法，比如速度、多读、慢读、列读……不管你采用哪一种读书方法，最终都要回归到“行动”二字上，正如陆...
                                    </p>
                                    <div class="meta">
                                        <nuxt-link to="/collecton/123"  class="collection-tag">
                                            短篇小说
                                        </nuxt-link>
                                        <nuxt-link to="/p/123" class="color-change">
                                            <i class="fa fa-eye"></i>
                                            555
                                        </nuxt-link>
                                        <nuxt-link to="/p/123" class="color-change">
                                            <i class="fa fa-comments"></i>
                                            555
                                        </nuxt-link>
                                        <span>
                                           <i class="fa fa-heart"></i>
                                           200
                                        </span>
                                    </div>
                                </div>
                            </li>
                        </ul>
                    </div>
                    <!--阅读更多-->
                    <nuxt-link to="/" class="load-more">
                        阅读更多
                    </nuxt-link>
                    <!---->
                </div>
                <div class="col-4 aside">
                    <div class="board">
                        <nuxt-link to="/">
                            <img src="../assets/img/right-1.png" alt="">
                        </nuxt-link>
                        <nuxt-link to="/">
                            <img src="../assets/img/right-2.png" alt="">
                        </nuxt-link>
                        <nuxt-link to="/">
                            <img src="../assets/img/right-3.png" alt="">
                        </nuxt-link>
                        <nuxt-link to="/">
                            <img src="../assets/img/right-4.png" alt="">
                        </nuxt-link>
                        <nuxt-link to="/">
                            <img src="../assets/img/right-5.png" alt="">
                        </nuxt-link>
                    </div>
                    <nuxt-link to="/" class="download" id="popoverButton-sync" variant="primary">
                        <img src="../assets/img/zanshang1.png" alt="" style="float: left">
                        <div style="float: left;overflow: hidden;margin-top: 30px">
                            <span>喜欢作者就赞赏一下吧</span>
                        </div>
                        <b-popover :show.sync="showPop" target="popoverButton-sync" placement="top" triggers="hover focus">
                            <img src="../assets/img/zanshang.png" alt="" style="width: 276px">
                        </b-popover>
                    </nuxt-link>
                    <div class="recommend-author">

                        <div class="title">
                            <span>推荐作者</span>
                            <a href="javascript:void(0)" class="page-change" @click="rotate()">
                                <i class="fa fa-refresh" ref="refresh"></i>
                                换一批
                            </a>
                        </div>
                        <ul class="list">
                            <li>
                                <nuxt-link to="/u/123" class="avatar">
                                    <img src="../assets/img/default-avatar.jpg" alt="">
                                </nuxt-link>
                                <nuxt-link to="/u/123" class="follow">
                                    <i class="fa fa-plus"></i>
                                    关注

                                </nuxt-link>
                                <nuxt-link class="name" to="/u/123">
                                    甘忠祥
                                </nuxt-link>
                                <p>
                                    写了152.9k字·7.2k喜欢
                                </p>
                            </li>
                            <li>
                                <nuxt-link to="/u/123" class="avatar">
                                    <img src="../assets/img/default-avatar.jpg" alt="">
                                </nuxt-link>
                                <nuxt-link to="/u/123" class="follow">
                                    <i class="fa fa-plus"></i>
                                    关注

                                </nuxt-link>
                                <nuxt-link class="name" to="/u/123">
                                    甘忠祥
                                </nuxt-link>
                                <p>
                                    写了152.9k字·7.2k喜欢
                                </p>
                            </li>
                            <li>
                                <nuxt-link to="/u/123" class="avatar">
                                    <img src="../assets/img/default-avatar.jpg" alt="">
                                </nuxt-link>
                                <nuxt-link to="/u/123" class="follow">
                                    <i class="fa fa-plus"></i>
                                    关注

                                </nuxt-link>
                                <nuxt-link class="name" to="/u/123">
                                    甘忠祥
                                </nuxt-link>
                                <p>
                                    写了152.9k字·7.2k喜欢
                                </p>
                            </li>
                            <li>
                                <nuxt-link to="/u/123" class="avatar">
                                    <img src="../assets/img/default-avatar.jpg" alt="">
                                </nuxt-link>
                                <nuxt-link to="/u/123" class="follow">
                                    <i class="fa fa-plus"></i>
                                    关注

                                </nuxt-link>
                                <nuxt-link class="name" to="/u/123">
                                    甘忠祥
                                </nuxt-link>
                                <p>
                                    写了152.9k字·7.2k喜欢
                                </p>
                            </li>
                            <li>
                                <nuxt-link to="/u/123" class="avatar">
                                    <img src="../assets/img/default-avatar.jpg" alt="">
                                </nuxt-link>
                                <nuxt-link to="/u/123" class="follow">
                                    <i class="fa fa-plus"></i>
                                    关注

                                </nuxt-link>
                                <nuxt-link class="name" to="/u/123">
                                    逯灿灿
                                </nuxt-link>
                                <p>
                                    写了15.9k字·7.2k喜欢
                                </p>
                            </li>
                        </ul>
                        <nuxt-link to="/" class="find-more">
                            查看全部 <i class="fa fa-angle-right"></i>
                        </nuxt-link>
                    </div>
                </div>
            </div>
        </div>
        <footer class="my-container">
            <div class="row">
                <div class="col-12">
                    <ul class="footer-row">
                        <li>关于简书</li>
                        <span>·</span>
                        <li>联系我们</li>
                        <span>·</span>
                        <li>加入我们</li>
                        <span>·</span>
                        <li>简书出版</li>
                        <span>·</span>
                        <li>品牌与徽标</li>
                        <span>·</span>
                        <li>帮助中心</li>
                        <span>·</span>
                        <li>合作伙伴</li>
                    </ul>
                    <p class="footer-info">©版权所有 如果你支持或者喜欢请给作者一点小小的支持
                        <a href="https://github.com/GzxNydia">作者邮箱</a>
                    </p>
                </div>
            </div>
        </footer>
    </div>
</template>

<script>
    import myHeader from '~/components/myHeader'
    export default {
        name: "index",
        components:{
            myHeader
        },
        data(){
            return{
                banners:[
                    "/banner1.jpg",
                    "/banner2.jpg",
                    "/banner3.jpg",
                    "/banner4.jpg",
                    "/banner5.jpg",
                    "/banner6.jpg"
                ],
                showPop:false,
                swiperOption: {
                    loop: true,
                    slidesPerView: 'auto',
                    centeredSlides: true,
                    spaceBetween: 30,
                    autoplay:{
                        display:3000,
                        stopOnLastSlide:false,
                        disableOnInteraction:false
                    },
                    pagination: {
                        el: '.swiper-pagination',
                        clickable: true
                    },
                    navigation:{
                        nextEl:'.swiper-button-next',
                        prevEl:'.swiper-button-prev'
                    }
                },
                deg:360,
            }
        },
        mounted() {
        },
        methods:{
            rotate:function(){
                this.deg = this.deg + 360
                this.$refs.refresh.style.transform = `rotate(${this.deg}deg)`;
            }
        }

    }
</script>

<style>
    .swiper-pagination span.active{
        color: #969696!important;
    }
</style>