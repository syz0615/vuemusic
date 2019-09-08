<!-- 新歌榜，热歌榜，king歌榜的公共样式，收到三个文件传来的url在对应区域进行显示 -->
<template>
 <div class="board panels">
    <div class="panel hotsongs on">
      <ul class="list">
        <router-link tag="li" :to="{name:'MusicPlay',params:{songid:item.song_id}}" class="song url" v-for="(item,index) in currentData" :key="index">
          <div class="poster">
            <img :src="item.pic_big" :alt="item.title">
          </div>
          <div class="info">
            <div class="name">
                {{ item.title }}
            </div>
            <div class="author">{{ item.artist_name }}</div>
          </div>
        </router-link>
      </ul>

    <div class="more-songs url">
    <!-- 点更多跳转 不能是div  接收home的type参数，在morelist中接收musictype-->
            <!-- 在路由传递的过程中，将type传递给musictype ，将本页面的title传递到更多页面的title-->
      <router-link :to="{ name:'MoreList', params:{musictype:this.type,title:title}}"  tag="div">
            查看该榜单&gt;
        </router-link> 
    </div>

    </div>
  </div>
</template>

<script>
export default {
  name: 'Music_List',
  data () {
    return {
  		currentData:[]
    }
  },
  props:{     //传过来不同音乐榜单的url
  	url:{
  		type:String,
  		default:''
  	},
    title:{
      type:String,
      default:''
    },
    type:{
      type:String,
      default:''
    }
  },
  mounted(){   //网络秦秋
    const httpUrl = this.HOST+this.url;
    this.$axios.get(httpUrl)
      .then(res => {
        this.currentData = res.data.song_list
     })
      .catch(error => {
        console.log(error);
     })
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.board{
  margin-bottom: 10px;  /*与下方隔开点距离*/
}

.panel {
    border-top: 1px solid #eee;   /*列表中最上面与导航的一条线*/
    position: relative;
    top: -1px;
    display: block;
    background: #fff;
}

.list{
  padding: 20px;
  padding-top: 0;
}

.panel .list li {
    height: 60px;
    border-bottom: 1px solid #eee;
    padding-left: 0;
    display: flex;
    padding-top: 10px;
}

.panel .list li .poster {
    position: relative;
    width: 45px;
    margin-right: 8px;
}

.panel .list li .poster img {
    border: 1px solid #eee;
}
.info{
    flex: 1;
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
}
.info .name {
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
    font-size: 16px;
    color: #333;
}

.info .author {
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
    font-size: 12px;
    color: #999;
    margin-top: 2px;
}

.more-songs {
    color: #999;
    margin-top: 9px;
    font-size: 12px;
    text-align: center;
    height: 32px;
    line-height: 32px;
}


</style>