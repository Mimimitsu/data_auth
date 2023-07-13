<template>
	<view class="body">
		<!-- 标题 -->
		<view class="title">
			身份证注册
		</view>
		<!-- 头像选择 -->
		<view class="avatar-choose" @click="avatarChoose">
			<uni-icons type="camera-filled" size="30"></uni-icons>
		</view>
		<!-- 身份证表单 -->
		<view class="input-container">
			<view class="input-item">
				<text id="ID">身份证</text>
				<input type="text" v-model="ID" placeholder="18位身份证号码">
			</view>
		</view>
		<view class="line"> </view>
		<!-- 密码表单 -->
		<view class="input-container">
			<view class="input-item">
				<text id="password">密码</text>
				<input password type="text" v-model="passward" placeholder="填写密码">
			</view>
		</view>
		<view class="line"> </view>
		<!-- 协议勾选 -->
		<view class="agreement-container">
			<checkbox-group @change="checkBoxHandler">
				<label>
					<checkbox style="transform:scale(0.7)"/>
				</label>
			</checkbox-group>
			<text>我已阅读并同意</text>
			<text id="agree">《软件许可及服务协议》</text>
		</view>
		<view class="button-container">
			<button type="primary" @click="buttonHandler">同意并继续</button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				ID: "",
				passward: "",
				buttonFlag: [],
				// 登录账号密码合法验证
				accChecked: true,
				// 用户头像路径
				avatarPath: ""
			};
		},
		methods: {
			// 协议勾选事件处理
			checkBoxHandler(e) {
				this.buttonFlag = e.detail.value
			},
			buttonHandler() {
				// 表单输入内容处理
				if (this.ID.length == 0 || this.passward.length == 0) {
					uni.showToast({
						title: "请输入账号密码",
						icon: "error",
						duration: 1200
					})
					return
				}
				// 用户协议勾选检测
				if (this.buttonFlag.length == 0) {
					uni.showToast({
						title: "请勾选用户协议",
						icon:"error",
						duration: 1200
					})
					return
				}
				if (this.avatarPath.length == 0) {
					uni.showToast({
						title: "请选择头像",
						icon:"error",
						duration: 1200
					})
					return
				}
				// 表单信息处理
				console.log("身份证：" + this.ID);
				console.log("密码：" + this.passward);
				// 确认注册
				if (this.accChecked) {
					uni.showToast({
						title: "账号注册成功",
						icon: "success",
						duration: 1200
					})
					// 注册成功，返回登录界面
					setTimeout(() => {
						uni.navigateTo({
							url: "../login/login"
						})
					}, "1200")
				}else {
					uni.showToast({
						title: "error",
						icon: "error",
						duration: 1200
					})
					return
				}
			},
			// 头像选择事件
			avatarChoose() {
				uni.chooseImage({
					count: 1,
					sizeType: "compressed",
					sourceType: "album",
					success:function(res){
						this.avatarPath = res.tempFilePaths
						console.log(JSON.stringify(res.tempFilePaths))
					}
				})
			}
		}
	}
</script>

<style lang="scss">
	.body {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}
	.title {
		display: flex;
		justify-content: center;
		color: #000;
		font-size: 18px;
		font-style: normal;
		font-weight: 600;
		line-height: normal;
		margin-top: 30px;
		margin-bottom: 30px;
		letter-spacing: 1px;
	}
	.avatar-choose {
		padding: 30px;
		background-color: #F1F1F1;
		margin-bottom: 50px;
	}
	
	.input-container {
		display: flex;
		flex-direction: column;
		row-gap: 50px;
		position: relative;
		width: 100%;
		
	}
	.input-item {
		display: flex;
		
		#ID {
			position: relative;
			left: 12px;
		}
		#password {
			position: relative;
			left: 12px;
			margin-right: 18px;
		}
		input {
			position: relative;
			left: 50px;
		}
	}
	.line {
		margin-top: 10px;
		margin-bottom: 10px;
		width: 100%;
		height: 1px;
		background-color: #F1F1F1;
	}
	
	.agreement-container {
		display: flex;
		align-items: center;
		column-gap: 5px;
		margin-top: 80px;
		
		#agree {
			color: blue;
		}
	}
	
	button {
		width: 200px;
		height: 40px;
		display: flex;
		justify-content: center;
		align-items: center;
		margin-top: 20px;
	}
</style>
