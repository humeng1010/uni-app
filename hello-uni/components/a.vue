<template>
	<view>
		<view> 兄弟传值 B-A </view>
		{{data}}
	</view>
</template>

<script>
	export default {
		name:"ACom",
		mounted() {
			// 封装的全局事件总线
			uni.$on("testData",(value)=>{
				this.data = value
			})
		},
		data() {
			return {
				data:0
			};
		}
	}
</script>

<style>

</style>