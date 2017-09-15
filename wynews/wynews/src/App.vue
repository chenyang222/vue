<template>
  <div id="app">
  	
  	<view-box>
  	
  		<x-header
  			class="header"
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
  			<div class="tab"	>
  				<tab	>
					<tab-item selected>热点</tab-item>
					<tab-item>最新</tab-item>
					<tab-item>游戏</tab-item>
					<tab-item>音乐</tab-item>
					<tab-item>科技</tab-item>
					<tab-item>体育</tab-item>
				</tab>
  			</div>	
  		</scroller>
		
		<swiper
			:list="swiperList"
			v-model="swiperIndex"
			:loop='true'
		>
			
		</swiper>
		
		<marquee class="my-marquee">
			<marquee-item
				v-for='list in marqueeList'
			>{{ list.title }}</marquee-item>
		</marquee>
		
		<panel
			:list="dateList"
		>
			
		</panel>
		
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


import {ViewBox,XHeader,Tabbar,TabbarItem,Tab,TabItem,Scroller,Swiper,Marquee,MarqueeItem,Panel} from 'vux';

export default {
  name: 'app',
  components:{
  	ViewBox,
  	XHeader,
  	Tabbar,
  	TabbarItem,
  	Tab,
  	TabItem,
  	Scroller,
  	Swiper,
  	Marquee,
  	MarqueeItem,
  	Panel
  },
  created(){
  	//http://3g.163.com/touch/jsonp/sy/recommend/0-9.html
  	this.$jsonp('http://3g.163.com/touch/jsonp/sy/recommend/0-9.html').then( data =>{
  		
  		console.log(data)
  		//return
  		this.swiperList = data.focus.filter( item => {
  			return item.addata === null;
  		}).map(item =>{
  			return{
  				url:item.link,
  				img:item.picInfo[0].url,
  				title:item.title
  			}
  		})
  		
  		
  		this.dateList = data.focus.filter( item => {
  			return item.addata === null;
  		}).map(item =>{
  			return{
  				src:item.picInfo[0].url,
  				title:item.title,
  				desc:item.digest,
  				url:item.link
  			}
  		})
  	});
  	
   	this.$jsonp('http://3g.163.com/touch/jsonp/sy/recommend/0-9.html').then( data =>{
  		
  		this.marqueeList = data.live.filter( item => {
  			return item.addata === null;
  		}).map(item =>{
  			return{
  				title:item.title
  			}
  		})
  	}); 	
  	
  	
  },
  data(){
  	
  	return{
		swiperList:[],
		swiperIndex:1,
		dateList:[],
		marqueeList:[]
		}
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
			margin-top: 44px;
		}
		.header{
			position: absolute;
			left: 0;
			top: 0;
			width: 100%;
			z-index: 9;
		}
		.weui-media-box_appmsg .weui-media-box__hd img{
			width: 102px;
			height: 78px;
		}	
		.weui-media-box_appmsg .weui-media-box__hd{
			width: 100px;
		}
		.vux-marquee-box li{
			line-height: 25px;
  			padding-left: 5px;
		}
	}

</style>
