<template>
  <div class="news_list">
     <MusicList :url="url" :title="title" :type="type"/>
  </div>
</template>

<script>

import MusicList from '../../components/Music_List'

export default {
  name: 'news_list',
  components:{
  	MusicList
  },
  data () {
    return {
  		url:'/v1/restserver/ting?method=baidu.ting.billboard.billList&type=1&size=5&offset=0',
      title:'新歌榜',
      type:'1'
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>