<template>
	<view>
		<!-- 整个登录框的容器 -->
		<view class="login-container">
			<view class="login-title">
				数据授权应用平台
			</view>
			<view class="login-box">
				<view class="box-title-item">
					登录
				</view>
				<!-- 表单信息区域 -->
				<view class="input-box">
					<view class="input-box-left">
						<view class="input-box-left-item">
							身份证号码
						</view>
						<view class="input-box-left-item">
							密码
						</view>
					</view>
					<view class="input-box-right">
						<input type="text" v-model="ID">
						<input password type="text" confirm-type="done" v-model="passward">
					</view>
				</view>
				<!-- 登录选项区域 -->
				<view class="login-checkbox">
						<checkbox-group @change="checkBoxHandler">
							<label>
								<checkbox/>
							</label>
						</checkbox-group>
						<text>登录注册表示同意</text>
						<text id="agree" @click="agreeNaviagte">用户协议及隐私条款</text>
				</view>
				<!-- 登录按钮区域 -->
				<view class="login-button-box">
					<button type="primary" @click="buttonHandler">登录</button>
					<text id="forget">忘记密码</text>
					<text id="register">用户注册</text>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				// 勾选协议检测
				buttonFlag: [],
				// 用户身份证
				ID: "",
				// 用户密码
				passward: "",
				// 账号密码核对检测
				accChecked: true
				
			};
		},
		methods: {
			// 用户协议跳转点击事件处理
			agreeNaviagte() {
				uni.navigateTo({
					url: '../agree/agree'
				})
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
				// 表单信息处理
				console.log("身份证：" + this.ID);
				console.log("密码：" + this.passward);
				// 登录跳转
				if (this.accChecked) {
					uni.navigateTo({
						url: "../face_recognition/face_recognition"
					})
				} else{
					uni.showToast({
						title: "账号或密码错误",
						icon:"error",
						duration: 1200
					})
				}
			},
			checkBoxHandler(e) {
				this.buttonFlag = e.detail.value
			}
		}
	}
</script>

<style lang="scss">
	.login-container {
		display: flex;
		flex-direction: column;
		align-items: flex-start;
		gap: 20px;
		height: 360;
		margin: 0 auto;
		position: absolute;
		top: 50%;
		left: 50%;
		transform: translate(-50%, -60%);
		
		.login-title {
			width: 326px;
			color: #000;
			font-size: 30px;
			font-style: normal;
			font-weight: 700;
			line-height: normal;
		}
		
		.login-box {
			display: flex;
			flex-direction: column;
			width: 326px;
			height: 210px;
			border-radius: 15px;
			border: 1px solid #888;
			background: #F1F1F1;
			
			.box-title-item {
				height: 50px;
				padding-top: 10px;
				padding-left: 20px;
				color: #000;
				font-size: 25px;
				font-style: normal;
				font-weight: 400;
				line-height: normal;
			}
			
			.input-box {
				display: flex;
				
				.input-box-left {
					width: 91px;
					display: flex;
					flex-direction: column;
					justify-content: center;
					gap: 16rpx;
					padding-left: 15px;
					color: #000;
					font-size: 15px;
					font-style: normal;
					font-weight: 400;
					line-height: normal;
				}
				
				.input-box-right {
					display: flex;
					flex-direction: column;
					gap: 7rpx;
					
					input {
						border: 1px solid black;
						background: #FFFFFF;
						width: 200px;
						height: 25px;
					}
				}
			}
			
			.login-checkbox {
				padding-top: 5px;
				font-size: 12px;
				display: flex;
				justify-content: center;
				align-items: center;
				
				checkbox {
					transform: scale(0.7);
				}
				
				#agree {
					margin-left: 5px;
					color: blue;
					text-decoration: underline;
				}
			}
			
			.login-button-box {
				
				button {
					width: 200px;
					height: 31px;
					display: flex;
					justify-content: center;
					align-items: center;
					letter-spacing: 20px;
					text-indent: 20px;
					border-radius: 0px;
				}
				
				#forget {
					position: absolute;
					left: 10px;
					font-size: 12px;
					color: #1AAD19;
				}
				
				#register {
					position: absolute;
					right: 10px;
					font-size: 12px;
					color: #1AAD19;
				}
			}
		}
	}
</style>
