<!-- 首页轮播图 -->
<template>
  <div class="banner">
     <swiper :options="swiperOption">
      <swiper-slide>
        <img src="../assets/img/b1.jpg" alt="">
      </swiper-slide>
      <swiper-slide>
        <img src="../assets/img/b2.jpg" alt="">
      </swiper-slide>
      <swiper-slide>
        <img src="../assets/img/b3.jpg" alt="">
      </swiper-slide>
      <div class="swiper-pagination"  slot="pagination"></div>
    </swiper>
  </div>
</template>

<script>
// 引入样式
import 'swiper/dist/css/swiper.css'
// 引入第三方库
import { swiper, swiperSlide } from 'vue-awesome-swiper'

export default {
  name: 'Swiper_Banner',
  components:{
  	swiper,
  	swiperSlide
  },
  data () {
    return {
  		swiperOption:{
  			// 分页器，图片下面的小点
  			pagination: {
  				el: '.swiper-pagination'
  			},
  			autoplay:true
  		}
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.banner{
  padding: 10px;
}
</style>