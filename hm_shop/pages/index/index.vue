<template>
	<view class="home">
		<!-- indicator-dots底部小圆点 -->
		<!-- circular是否采用衔接滑动，即播放到末尾后重新回到开头 -->
		<!-- autoplay自动切换 -->
		<!-- interval自动切换时间间隔 -->
		<swiper indicator-dots circular autoplay :interval="4000">
			<swiper-item v-for="item in swipers" :key="item.goods_id">
				<image :src="item.image_src"></image>
			</swiper-item>
		</swiper>
		<!-- 导航区 -->
		<view class="nav">
			<view class="nav_item">
				<view class="iconfont icon-ziyuan"></view>
				<text>超市</text>
			</view>
			<view class="nav_item">
				<view class="iconfont icon-guanyuwomen"></view>
				<text>联系我们</text>
			</view>
			<view class="nav_item">
				<view class="iconfont icon-tupian"></view>
				<text>社区图片</text>
			</view>
			<view class="nav_item">
				<view class="iconfont icon-shipin"></view>
				<text>学习视频</text>
			</view>
		</view>
		<!-- 推荐商品区 -->
		<view class="hot_goods">
			<view class="tit">推荐商品</view>
			<view class="goods_list">
				<view class="goods_item" v-for="good in goods" :key="good.goods_id">
					<image src = "https://img13.360buyimg.com/n1/s450x450_jfs/t1/78149/38/20599/418414/62b5688cEf1797095/3236d8a3352fd964.jpg.avif"></image>
					<view class="price">
						<text>￥4199</text>
						<text>￥3999</text>
					</view>
					<view class="name">
						HUAWEI nova 10 Pro 【内置100W华为超级快充】前置6000万追焦双摄 轻薄机身 256GB 10号色 华为手机
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				swipers: [],
				goods:[],
			}
		},
		onLoad() {
			this.getSwipers();
			this.getHotGoods();
		},
		methods: {
			// 获取轮播图
			async getSwipers() {
				// console.log("获取轮播图");
				const res = await this.$myRequest({
					url: "/api/public/v1/home/swiperdata",
				})
				// console.log(res);
				this.swipers = res.data.message;
			},
			// 获取热门商品
			async getHotGoods(){
			 const res = await this.$myRequest({
					url:"/api/public/v1/home/floordata",
				})
				console.log(res);
				this.goods = res.data.message
			}
		}
	}
</script>

<style lang="scss">
	.home{
		swiper{
			width: 750rpx;
			height: 380rpx;
			image{
				height: 100%;
				width: 100%;
			}
		}
	}
	.nav{
		display: flex;
		.nav_item{
			width: 25%;
			text-align: center;
			view{
				width: 120rpx;
				height: 120rpx;
				background: $shop-color;
				border-radius: 50%;
				margin: 10px auto;
				line-height: 120rpx;
				color: #fff;
				font-size: 50rpx;
			}
			.icon-tupian{
				font-size: 45rpx;
			}
			text{
				font-size: 30rpx;
			}
		}
	}
	.hot_goods{
		background: #eee;
		overflow: hidden;
		margin-top: 10px;
		.tit{
			height: 50px;
			line-height: 50px;
			color: $shop-color;
			text-align: center;
			letter-spacing: 20px;
			background: #fff;
			margin: 7rpx 0;
		}
		
		.goods_list{
			padding: 0 15rpx;
			display: flex;
			flex-wrap: wrap;
			justify-content: space-between;
			.goods_item{
				background: #fff;
				width: 355rpx;
				margin: 10rpx 0;
				padding: 15rpx;
				box-sizing: border-box;
				image{
					width: 80%;
					height: 150px;
					display: block;
					margin: 0 auto;
				}
				.price{
					color: $shop-color;
					font-size: 36rpx;
					text:nth-child(2){
						color: #ccc;
						font-size: 28rpx;
						margin-left: 17rpx;
						text-decoration: line-through;
					}
				}
				.name{
					font-size: 28rpx;
					line-height: 50rpx;
					padding-bottom: 15rpx;
					padding-top: 10rpx;
				}
			}
		}
	}

</style>
