<template>
	<view>
		<button @click="sendData">点击我(兄弟传值)</button>
	</view>
</template>

<script>
	export default {
		name:"BCom",
		data() {
			return {
				
			};
		},
		methods:{
			sendData(){
				uni.$emit("testData",666)
			}
		}
	}
</script>

<style>

</style>