<template>
    <div>
        <my-header></my-header>
        <div class="index my-container">
            <div class="row">
                <div class="col-8 main">
                    <div v-swiper:mySwiper="swiperOption">
                        <div class="swiper-wrapper banner">
                            <div class="swiper-slide" v-for="banner in banners">
                                <img :src="banner">
                            </div>
                        </div>
                        <div class="swiper-pagination swiper-pagination-white"></div>
                        <div class="swiper-button-prev swiper-button-white"></div>
                        <div class="swiper-button-next swiper-button-white"></div>
                    </div>
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
                </div>
            </div>
        </div>
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
                }
            }
        },
        mounted() {
        }

    }
</script>

<style>
    .swiper-pagination span.active{
        color: #969696!important;
    }
</style>