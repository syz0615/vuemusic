<!-- hot_list.vue -->
<template>
  <div class="hot_list">

	<MusicList  :url="url" :title="title" :type="type" />
  </div>
</template>

<script>

import MusicList from "../../components/Music_List"

export default {
  name: 'Hot_List',
  components:{
  	MusicList
  },
  data () {
    return {
  		url:'/v1/restserver/ting?method=baidu.ting.billboard.billList&type=2&size=5&offset=0',
      title:'热歌榜',
      type:'2'
    }
  }


}
</script>


<style scoped>

/*样式来自于Music_List.vue*/

</style>