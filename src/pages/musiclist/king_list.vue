<template>
  <div class="king_list">
     
	<MusicList :url="url" :title="title" :type="type"/>

  </div>
</template>

<script>

import MusicList from '../../components/Music_List'

export default {
  name: 'king_list',
  components:{
  	MusicList
  },
  data () {
    return {
  		url:'/v1/restserver/ting?method=baidu.ting.billboard.billList&type=21&size=5&offset=0',
      title:'king歌榜',
      type:'21'
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>