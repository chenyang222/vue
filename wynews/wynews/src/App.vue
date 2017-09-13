<template>
  <div id="app">
  	
  	<view-box>
  		<x-header></x-header>
		  	
  	</view-box>
    <router-view></router-view>
  </div>
</template>

<script>


import {ViewBox , XHeader} from 'vux';

export default {
  name: 'app',
  components:{
  	ViewBox,
  	XHeader
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
	}

</style>
