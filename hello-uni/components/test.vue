<template>
	<view>
		这是test组件
		<view>
			<text>父组件传递的{{age}}</text>
		</view>
		<view>
			<button @click="sendValue">点击我给父组件传值自定义事件1@</button>
			<button @click="sendValue2">点击我给父组件传值自定义事件2ref</button>
		</view>
	</view>
	
</template>

<script>
	export default {
		name:"test",
		props:["age"],
		data() {
			return {
				
			};
		},
		methods:{
			sendValue(){
				this.$emit("myEvent",666)
			},
			sendValue2(){
				this.$emit("test",888)
			}
		}
	}
</script>

<style>

</style>