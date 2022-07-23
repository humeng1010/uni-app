<template>
	<view>
		<view>
			{{message}}
		</view>
		<view>
			<ul>
				<li v-for="p in person" :key="p.id">
					姓名{{p.name}} 年龄{{p.age}}
				</li>
			</ul>
			<button type="primary" @click="test($event,666)">点击</button>
		</view>
	</view>
</template>

<script>
	export default{
		data(){
			return {
				message:"数据",
				person:[
					{
						id:"001",
						name:"zs",
						age:20
					},
					{
						id:"002",
						name:"ls",
						age:22
					}
				]
			}
		},
		methods:{
			test(e,number){
				// event
				console.log("哈哈",e,number);
			}
		}
	}
</script>

<style>
</style>