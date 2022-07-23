<template>
	<view class="content">
		<!-- 父传子 -->
		<Test :age="age" @myEvent="getValue" ref="test"></Test>
		<ACom></ACom>
		<BCom></BCom>
		<uni-calendar 
		    :insert="true"
		    :lunar="true" 
		    :start-date="'1970-0-0'"
		    :end-date="'2050-5-20'"
		    @change="change"
			
		     />
	</view>
</template>

<script>
	import Test from "../../components/test.vue";
	import ACom from "../../components/a.vue";
	import BCom from "../../components/b.vue";
	export default {
		data() {
			return {
				title: 'Hello',
				age:20
			}
		},
		mounted() {
			this.$refs.test.$on("test",(value)=>{
				console.log("父组件接收到了",value);
				this.age = value;
			})
		},
		methods: {
			getValue(value){
				console.log("父组件接收到了",value);
				this.age = value;
			},
			change(e){
				console.log(e);
			}
		},
		components:{
			Test,
			ACom,
			BCom,
		},
		onLoad(options) {
			console.log("页面加载了",options);
		},
		onShow() {
			console.log("页面显示了");
		},
		onReady() {
			console.log("页面初次渲染完成了");
		},
		onHide() {
			console.log("页面隐藏了");
		},
		
	}
</script>

<style>
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}

	.logo {
		height: 200rpx;
		width: 200rpx;
		margin-top: 200rpx;
		margin-left: auto;
		margin-right: auto;
		margin-bottom: 50rpx;
	}

	.text-area {
		display: flex;
		justify-content: center;
	}

	.title {
		font-size: 36rpx;
		color: #8f8f94;
	}
</style>
