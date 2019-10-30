网址：https://github.com/surmon-china/vue-awesome-swiper

各种案例： https://github.surmon.me/vue-awesome-swiper/

1.安装：npm install vue-awesome-swiper --save；
2.在man.js引入
=====
    import VueAwesomeSwiper from 'vue-awesome-swiper'

    import 'swiper/dist/css/swiper.css'

    Vue.use(VueAwesomeSwiper)
======

3.在自己的组件内引入：
<script>
    import { swiper, swiperSlide } from 'vue-awesome-swiper'
    export default {
data(){
    return{
        swiperOption: {
          // some swiper options/callbacks
          // 所有的参数同 swiper 官方 api 参数
          // ...
           nextEl: '.swiper-button-next',
            prevEl: '.swiper-button-prev'
        }
    }
},

 computed: {
      swiper() {
        return this.$refs.mySwiper.swiper
      }
},
mounted() {
      // current swiper instance
      // 然后你就可以使用当前上下文内的swiper对象去做你想做的事了
      console.log('this is current swiper instance object', this.swiper)
      this.swiper.slideTo(3, 1000, false)
}
}
</script>
<template>
  <div class="q" >
        <swiper :options="swiperOption" ref="mySwiper">
            <swiper-slide>
                 <div class="w" >
                        <img src="../../../static/img1/1.png" alt="">
                </div>
            </swiper-slide>
            <swiper-slide>
                 <div class="w" >
                        <img src="../../../static/img1/2.png" alt="">
                </div>
            </swiper-slide>
            <div class="swiper-pagination"  slot="pagination"></div>
               <div class="swiper-button-prev" slot="button-prev"></div>
                <div class="swiper-button-next" slot="button-next"></div>
        </swiper>
  </div>
</template>