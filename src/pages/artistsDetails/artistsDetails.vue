<!-- 歌手的歌曲详情页面 引入title头像和list歌手的歌曲列表-->
<template>
  <div class="musicplay">
	<Title :name="this.$route.params.name" :avatar="this.$route.params.avatar"/>
	<List :ting_uid="this.$route.params.ting_uid"/>
  </div>
</template>

<script>
// 引入标题和图片
import Title from "../../components/details/title"
import List from "../../components/details/list"

export default {
  name: 'details',

  data () {
    return {
   
    }
  },
  components:{
  	Title,
  	List 
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>


</style>