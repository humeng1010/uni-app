<template>
	<view>
		<button @click="get">发送get请求</button>
		<button type="primary" @click="setStorage">存储本地数据</button>
		<button type="primary" @click="getStorage">获取本地数据</button>
		<button type="warn" @click="removeId">移除id</button>
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
	export default {
		data() {
			return {
				list: ['前端', "后端", "测试"]
			}
		},
		onPullDownRefresh() {
			// 下拉刷新数据，等待1秒更新
			setTimeout(() => {
				const p = ["唱", "跳", "rap", "篮球"];
				const p1 = ["弹", "说", "吹", "唱"];
				this.list.push(...p, ...p1);
				uni.stopPullDownRefresh();
			}, 100);

		},
		onReachBottom() {
			console.log("页面触底了");
			uni.startPullDownRefresh()
		},
		methods: {
			refreshList() {
				uni.startPullDownRefresh();
			},
			get() {
				uni.request({
					url: "https://api-hmugo-web.itheima.net/api/public/v1/home/swiperdata",
					success(res) {
						console.log(res);
					}
				});

			},
			setStorage() {
				// uni.setStorage({
				// 	key: "id",
				// 	data: 10,
				// 	success(res) {
				// 		console.log(res);
				// 	}
				// })
				uni.setStorageSync("id",100)
			},
			getStorage() {
				uni.getStorage({
					key: "id",
					// 完成后回调
					complete(res) {
						if (res.data) {
							console.log("获取数据成功", res);
						} else {
							console.log("获取数据失败", res.errMsg);
						}
					},
					// 只有成功才回调
					// success(res){
					// 	console.log(res);
					// },
				})
			},
			removeId(){
				uni.removeStorage({
					key:"id",
					complete(res){
						console.log(res);
					}
				})
			}
		}
	}
</script>

<style>
	.box-item li {
		height: 750px;
		/* line-height: 100px; */
	}
</style>
