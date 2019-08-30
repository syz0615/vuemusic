<template>
  <div class="lrcContainer">
	<div class="lrc" ref="lrc">
		{{getAllkey}}
		      <!--
        11  11
        12
        13  13
        14
        15  15

        117    117
        118
        119
        120
        121    121
        122
        123    123
     -->
			<!-- item就是一段一段的歌词 index是每段歌词的序号，从0开始 -->
			<!-- key是每段歌词开始的时间 parseInt将时间变成整数 -->
		<p class="lrc-p" :class="{active:parseInt(currentTime)>=keyArr[index]&&parseInt(currentTime)<keyArr[index+1]}" v-for="(item,key,index) in lrcData" :key="index">{{item}} {{srcollLrc(key,index)}}</p>

	</div>
  </div>
</template>

<script>
export default {
  name: 'lrc',

  data () {
    return {
   		lrc:{},
   		lrcData:{},
   		keyArr:[]   //用于存放key值，显示对应歌词用
    }
  },
  props:{
  	songid:{
  		type:[String,Number],
  		default:''
  	},
  	currentTime:{
  		type:Number,
  		default:0
  	},
  	duratonTime:{
  		type:Number,
  		default:0
  	}
  },
  mounted(){
  	const LRCUrl = this.HOST + "/v1/restserver/ting?method=baidu.ting.song.lry&songid=" + this.songid;
  	this.$axios.get(LRCUrl)
  	.then(res=> {
  		console.log(res.data);
  		this.lrc = res.data;

       // 数据格式处理
       var lyrics = res.data.lrcContent.split("\n");
        var lrcObj = {};
        for(var i = 0 ;i<lyrics.length;i++){
          var lyric = decodeURIComponent(lyrics[i]);
          var timeReg = /\[\d*:\d*((\.|\:)\d*)*\]/g;
          var timeRegExpArr = lyric.match(timeReg);
          if(!timeRegExpArr)continue;
          var clause = lyric.replace(timeReg,'');
             for(var k = 0,h = timeRegExpArr.length;k < h;k++) {
                 var t = timeRegExpArr[k];
                 var min = Number(String(t.match(/\[\d*/i)).slice(1)),
                     sec = Number(String(t.match(/\:\d*/i)).slice(1));
                 var time = min * 60 + sec;
                 lrcObj[time] = clause;
             }
           }
           this.lrcData = lrcObj;
  		
  	})
  	.catch(error=>{
  		console.log(error);
  	})
  },

  computed: {
  	getAllkey(){   //用于存放所有key值
  		for(var i in this.lrcData){
  			this.keyArr.push(i);
  		}
  	}
  },

  methods:{
  	srcollLrc(key,index){
      const lrcDiv = this.$refs.lrc    //获取到原生div
       if(key < this.currentTime && key > this.currentTime - (this.keyArr[index+1] - this.keyArr[index])){
       		//往上动所以是负的
           lrcDiv.style.top = -((index-2)*30)+"px"  
       }
    }

  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.lrcContainer{
  width: 100%;
  height: 150px;
  overflow: hidden;
  position: relative;
}

.lrc{
	width: 100%;
  position: absolute;
  top: 0;
}
.active{
  color: red !important;
  font-size: 18px;
}
.lrc-p{
  height: 30px;
	line-height: 30px;
}

.up30{
	margin-top: -30px;
}

</style>