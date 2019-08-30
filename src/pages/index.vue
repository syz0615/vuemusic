<template>
  <div class="index">
     <ul>
		<li>
			<router-link to="/home">
				<img src="../assets/logo-ea5.png">
			</router-link>
		</li>

		<li>
			<router-link to="/artists">
          		歌手
        	</router-link>
		</li>

		<li>
 			<router-link to="/listcate">
         	 	榜单
       		</router-link>
		</li>

		<li>
			<router-link to="/ucenter">
          		我的
        	</router-link>
		</li>
	        
		<li>
			<router-link to="/search">
	          搜索
	        </router-link>
		</li>
     </ul>
	 <!-- 在导航栏下显示各个页面的内容 -->
    <router-view />
  </div>
</template>

<script>


export default {
  name: 'Index',
  data () {
    return {
     
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.index img {
	width: 26px;
	height: 26px;
}

.index ul {
	display: flex;
	line-height: 50px;
	background: #f9f9f9;
	height: 50px;
}

.index ul li {
	text-align: center;
	flex: 1;
}
</style>