<template>
	<view class="rec-container">
		<camera device-position="front" flash="off" @error="error" style="width: 100%; height: 300px;">
		</camera>
		<button type="primary" @click="takePhoto">识别</button>
	</view>
</template>

<script>
	import {
		pathToBase64,
		base64ToPath
	} from 'image-tools'
	export default {
		data() {
			return {
				// 图片base64编码结果
				imgData: null,
				// 后端识别结果判断
				recResults: true
			};
		},
		methods: {
			// 拍照识别人脸方法
			takePhoto() {
				const ctx = uni.createCameraContext();
				// 获取实时人脸照片
				ctx.takePhoto({
					quality: 'high',
					success: (res) => {
						var src = res.tempImagePath
						console.log(src);
						// 获取图片base64
						pathToBase64(src).then(base64 => 
							{
								this.imgData = base64
							})
							.catch(error => {
								console.error(error)
							})
					}
				});
				// 接收后端处理结果
				
				// 判断是否是本人登录
				if (this.recResults) {
					// 登录成功, 跳转至首页
					uni.showToast({
						title: "人脸识别成功",
						icon: "success",
						duration: 1200
					})
					uni.navigateTo({
						url: "../homepage/homepage"
					})
				} else {
					// 登录失败, 重新识别
					uni.showToast({
						title: "人脸认证失败",
						icon: "error",
						duration: 1200
					})
				}
			},
			error(e) {
				console.log(e.detail);
			},
		}
	}
</script>

<style lang="scss">
	.rec-container {
		position: absolute;
		top: 50%;
		left: 50%;
		transform: translate(-50%, -70%);
	}
	button {
		margin-top: 10px;
		display: flex;
		align-items: center;
		justify-content: center;
		width: 200px;
		height: 31px;
		letter-spacing: 20px;
		text-indent: 20px;
		border-radius: 0px;
	}
</style>