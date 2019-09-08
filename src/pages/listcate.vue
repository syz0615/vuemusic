<!-- 导航榜单的页面 -->
<template lang="html">
  <div>
    <ListCate_List :key="index" v-for="(item,index) in musicTypeJSON" :musicType="item" />
  </div>
</template>

<script>

import MusicType from "../assets/data/musictype.json"
import ListCate_List from "../components/ListCate_List"

export default {
  data(){
   return{
     musicTypeJSON:[]
   }
  },
  components:{
  	MusicType,
    ListCate_List
  },
  created(){
    this.musicTypeJSON = MusicType.currentType
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>