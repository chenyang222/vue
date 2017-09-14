<template>
  <div id="app">
  	
  	<view-box>
  	
  		<x-header
  			slot="header"
  			:left-options="{showBack:false,backText:'返回'}"
  		>
  			<div slot='left'>直播</div>
  			<div>网易</div>
  			<div slot='right'>搜索</div>
  		</x-header>
  		
  		<scroller
  			:lock-y='true'
  		>
  			<div>
  				<tab	
					class="tab"	
				>
					<tab-item selected>热点</tab-item>
					<tab-item>最新</tab-item>
					<tab-item>游戏</tab-item>
					<tab-item>音乐</tab-item>
					<tab-item>科技</tab-item>
					<tab-item>体育</tab-item>
				</tab>
  			</div>	
  		</scroller>
		
		
		 <tabbar>
		 	<tabbar-item>
				<img src="./assets/icon_nav_button.png" alt="" slot="icon">
				<span slot='label'>首页</span>
		 	</tabbar-item>
		 	<tabbar-item>
		 		<img src="./assets/icon_nav_article.png" alt="" slot="icon">
		 		<span slot='label'>推荐</span>
		 	</tabbar-item>
		 	<tabbar-item>
		 		<img src="./assets/icon_nav_cell.png" alt="" slot="icon">
		 		<span slot='label'>我的</span>
		 	</tabbar-item>		 	
		 </tabbar>
		 
  	</view-box>
    <router-view></router-view>
  </div>
</template>

<script>


import {ViewBox,XHeader,Tabbar,TabbarItem,Tab,TabItem,Scroller} from 'vux';

export default {
  name: 'app',
  components:{
  	ViewBox,
  	XHeader,
  	Tabbar,
  	TabbarItem,
  	Tab,
  	TabItem,
  	Scroller
  }
}
</script>

<style lang="less">
	
	@import '~vux/src/styles/reset.less';

	html,body{
		margin: 0;
		padding: 0;
		width: 100%;
		height: 100%;
		overflow-x: hidden;
	}
	#app{
		height: 100%;
		overflow: hidden;
		.tab{
			width: 1200px;
			position: relative;
		}
	}

</style>
