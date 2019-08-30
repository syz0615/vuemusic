<!-- news_list.vue 新歌速递-->
<template>
 <div class="mod-albums">
    <div class="hd log url">
    <h2>新歌速递</h2>
	    <div>
			更多
	    </div>
    </div>

    <div class="container">
   		<div class="gallery">
        	<div class="scroller">
        	 <router-link tag="div" :to="{name:'MusicPlay',params:{songid:item.song_id}}" class="card url" v-for="(item,index) in todayRecommend" :key="index">
				<div class="album">  <!--alt中是图片的名称，不显示-->
				 	<img :src="item.pic_big" :alt="item.title">
                    <div class="name">{{ item.title }}</div>
                    <!-- 作者姓名 -->
                    <!-- <div class="author">{{ item.artist_name }}</div> -->
				</div>
				</router-link>
        	</div>
        </div>
     </div>
  </div>
</template>

<script>
export default {
  name: 'News_Music',
  data () {
    return {
  		todayRecommend:[]
    }
  },
  mounted() {
	 var url = this.HOST + "/v1/restserver/ting?method=baidu.ting.billboard.billList&type=2&size=3&offset=0"
	 this.$axios.get(url)
	 .then(res=> {
	 	this.todayRecommend = res.data.song_list;
	   })
	 .catch(error=> {
	   console.log(error)
	  })
	}
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.mod-albums {
    background-color: #fff;
    padding: 10px 17px;
    margin-top: 15px;   /*距上一视图的距离*/
}

.hd {
    display: flex;
    margin: 14px 0 18px 0;
}

.hd h2 {
    -webkit-box-flex: 1;
    -webkit-flex: 1;
    flex: 1;
    margin: 0;
    padding: 0;
    font-size: 20px;
}

.hd div {
    width: 64px;
    font-size: 12px;
    text-align: right;
}

.mod-albums .gallery {
    overflow: hidden;
    margin: 0 -5px;
}

 .mod-albums .gallery .card {
    width: 33.3%;  /*一行显示三张图片*/
    float: left;
    -webkit-box-sizing: border-box;
    box-sizing: border-box;
    padding: 0 5px 10px;  /*图片与图片之间就空隙*/
}

.mod-albums .gallery .card .album {
  position: relative;
}

.mod-albums .gallery .card img {
    width: 100%;
    height: auto;
    border: 1px solid #eee;
}

.mod-albums .gallery .card .name {
    font-size: 12px;
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
    margin-top: 4px;
    line-height: 14px;
    max-height: 28px;
    margin-bottom: 2px;
}
.mod-albums .gallery .card .author {
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
    color: #999;
    font-size: 12px;
    line-height: 12px;
}
</style>