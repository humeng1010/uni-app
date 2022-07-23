<template>
	<view>
		<view>导航跳转</view>
		<!-- 声明式 -->
		<navigator url="/pages/detail/detail?id=80">跳转到详情页</navigator>
		<!-- 跳转到TabBar页面 需要设置open-type -->
		<navigator url="/pages/message/message" open-type="switchTab">跳转到信息页</navigator>
		<navigator url="/pages/detail/detail" open-type="redirect">跳转到详情页</navigator>
		
		<!-- 编程式 -->
		<button @click="goDetail">跳转到详情页</button>
		<button @click="goMessage">跳转到信息页</button>
		<button type="warn" @click="redirectDetail">跳转到详情页并关闭当前页面</button>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		methods: {
			goDetail(){
				uni.navigateTo({
					url:"/pages/detail/detail"
				})
			},
			goMessage(){
				// 跳转到tabBar页面 并且关闭非TabBar页面
				uni.switchTab({
					url:"/pages/message/message"
				})
			},
			redirectDetail(){
				uni.redirectTo({
					url:"/pages/detail/detail"
				})
			}
		},
		onUnload(){
			console.log("当前页面关闭了");
		}
	}
</script>

<style>

</style>
