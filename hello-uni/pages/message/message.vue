<template>
	<view>
		<h1 class="title">iKun</h1>
		<button type="primary" size="mini" @click="chooseImg">上传图片</button>
		<image v-for="img in imgArr" :src="img" @click="previewImg(img)"></image>
		<!-- 条件编译，跨端兼容 -->
		<!-- #ifdef H5 -->
		<view>只在H5中展示</view>
		<!-- #endif -->
		<!-- #ifdef MP-WEIXIN -->
		<view>只在微信小程序中展示</view>
		<!-- #endif -->

	</view>
</template>

<script>
	export default {
		data() {
			return {
				imgArr: []
			}
		},
		methods: {
			chooseImg() {
				uni.chooseImage({
					// 限制5张
					count: 5,
					// 箭头函数调整this指向
					success: res => {
						console.log(res);
						this.imgArr.push(...res.tempFilePaths)
						// this.imgArr = [...this.imgArr,...res.tempFilePaths]
					}
				})
			},
			previewImg(current) {
				uni.previewImage({
					urls: this.imgArr,
					current,
					loop: true,
					indicator: "number"
				})
			}
		},
		onShow() {
			// #ifdef H5
			console.log("h5中显示");
			// #endif
			// #ifdef MP-WEIXIN
			console.log("微信小程序中显示");
			// #endif
		}
	}
</script>

<style>
	.title {
		text-align: center;
	}

	button {
		background: #6cf;
	}
</style>
