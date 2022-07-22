<template>
	<view>
		<!-- <view>
			<text>
				唱歌跳舞打篮球
			</text>
		</view>
		<view>
			selectable 控制文本是否可选
			<text selectable="true">
				唱歌跳舞打篮球
			</text>
		</view>
		<view>
			space 控制空格的大小
			<text selectable="true" space="ensp">
				唱歌    跳舞打篮球
			</text>
		</view> -->
		<view class="box2" hover-class="box2-active">
			<!-- hover-stop-propagation="true" 阻止事件冒泡 -->
		<view class="box" hover-class="box-active" :hover-stop-propagation="true" :hover-start-time="10" :hover-stay-time="100">
		</view>
		
		</view>
		<button>button</button>
		<button size="mini">button</button>
		<button type="primary" @click="showMsg">button</button>
		<button type="primary" @click="showMsg" plain>button</button>
		<button type="primary" @click="showMsg" plain disabled>button</button>
		<button type="primary" @click="showMsg" plain disabled loading>button</button>
		
		<image src="https://cdn.staticaly.com/gh/redyouzi/images-for-blog@main/img01/Vue与VueComponent关系.51e1tls3agk0.png"></image>
		<image mode="aspectFill" src="https://cdn.staticaly.com/gh/redyouzi/images-for-blog@main/img01/Vue与VueComponent关系.51e1tls3agk0.png"></image>
		<image mode="aspectFit" src="https://cdn.staticaly.com/gh/redyouzi/images-for-blog@main/img01/Vue与VueComponent关系.51e1tls3agk0.png"></image>
			
	</view>
	
</template>

<script>
		export default{
			methods:{
				showMsg(){
					console.log(666);
				}
			}
		}
</script>

<style>
	.box{
		width: 100px;
		height: 100px;
		background-color: blue;
	}
	.box2{
		width: 200px;
		height: 200px;
		background-color: black;
	}
	.box-active{
		background-color: red;
	}
	.box2-active{
		background-color: pink;
	}
</style>