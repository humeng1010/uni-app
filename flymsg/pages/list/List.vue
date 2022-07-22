<template>
	<view>
	<view>这是列表页</view>
	<view class="box-item">
		<ul>
			<li v-for="(l,index) in list" :key="index">{{l}}</li>
		</ul>
	</view>
	<button type="primary" @click="refreshList">刷新列表</button>
		
	</view>
	
</template>

<script>
	export default{
		data(){
			return {
				list:['前端',"后端","测试"]
			}
		},
		onPullDownRefresh() {
			// 下拉刷新数据，等待1秒更新
			setTimeout(()=> {
				const p = ["唱","跳","rap","篮球"];
				const p1 = ["弹","说","吹","唱"];
				this.list.push(...p,...p1);
				uni.stopPullDownRefresh();
			}, 100);
			
		},
		onReachBottom() {
				console.log("页面触底了");
				uni.startPullDownRefresh()
		},
		methods:{
			refreshList(){
				uni.startPullDownRefresh();
			}
		}
	}
</script>

<style>
	.box-item li{
		height: 750px;
		/* line-height: 100px; */
	}
</style>