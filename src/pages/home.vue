<!-- home.vue index.vue下面的二级页面-->
<template>
  <div class="home">
    <!-- home中调用Today_Recommend ，只指定type类型，url地址在Today_Recommend中声明-->

     <Today_Recommend title='今日推荐' type='1'/>
     <News_Music title='新歌速递' type='2' />
     <SwiperBanner />
     <MusicListNav />

     <!-- 显示三级子菜单 keep-alive的作用是第一次点击进行加载数据，点击第二次不需要加载数据-->
     <keep-alive>
        <router-view />
     </keep-alive> 
     
     <Today_Recommend title='热门歌单' type='24'/>
  </div>
</template>

<script>
import Today_Recommend from '../components/Today_Recommend'
import News_Music from '../components/News_Music'
import SwiperBanner from '../components/Swiper_Banner'
import MusicListNav from './musiclist/music_listnav'

export default {
  name: 'Home',
  components:{
  	Today_Recommend,
  	News_Music,
  	SwiperBanner,
  	MusicListNav

  },
  data () {
    return {
   
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>


</style>