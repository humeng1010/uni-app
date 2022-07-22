<script>
	export default {
		// 生命周期函数
		// 应用启动渲染出来触发onLaunch(只触发一次)
		onLaunch() {
			console.log('App 已启动')
		},
		// app 显示出来触发
		onShow() {
			console.log('App 显示')
		},
		// app 隐藏触发
		onHide() {
			console.log('App 隐藏')
		},
		// 报错触发
		onError(e) {
			console.log("出现异常了",e);
		}
	}
</script>

<style>
	/*每个页面公共css */
	@import url("./static/fonts/iconfont.css");
	.box1{
		background: pink;
	}
</style>
