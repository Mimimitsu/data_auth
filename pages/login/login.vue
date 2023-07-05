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
				<!-- 账号密码表单框 -->
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
						<input type="text" placeholder="身份证号码">
						<input password type="text" placeholder="密码">
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
				
			};
		}
	}
</script>

<style lang="scss">
	.login-container {
		display: flex;
		flex-direction: column;
		align-items: flex-start;
		gap: 30px;
		background: greenyellow;
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
			font-family: Inter;
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
				height: 62px;
				padding-top: 20px;
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
					// align-items: center;
					justify-content: center;
					gap: 16rpx;
					padding-left: 15px;
					color: #000;
					font-size: 15px;
					font-family: Inter;
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
		}
	}
</style>
