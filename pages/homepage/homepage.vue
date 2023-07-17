<template>
	<view class="body">
		<!-- 用户基本信息区域 -->
		<view class="user-info-container">
			<!-- 用户头像 -->
			<view class="user-avatar-box">
				<img id="img" src="/static/user_icon.jpg">
			</view>
			<!-- 用户名称、注册时间 -->
			<view class="user-info-box">
				<view class="user-name">
					用户名
				</view>
				<view class="register-time">
					注册时间：2023-06-20
				</view>
			</view>
			<!-- 用户二维码 -->
			<view class="user-qrcode-box">
				<img id="qrcode" src="/static/qrcode_img.png">
				<uni-icons type="right"></uni-icons>
			</view>
		</view>
		<!-- 选项设置区域 -->
		<view class="option-container">
			<view class="option-item">
				<uni-icons id="option" type="chat" size="25"></uni-icons>
				授权消息
				<uni-icons id="option-arrow" type="right"></uni-icons>
			</view>
			<view class="option-item">
				<uni-icons id="option" type="list" size="25"></uni-icons>
				授权记录
				<uni-icons id="option-arrow" type="right"></uni-icons>
			</view>
			<view class="option-item">
				<uni-icons id="option" type="person" size="25"></uni-icons>
				个人信息
				<uni-icons id="option-arrow" type="right"></uni-icons>
			</view>
			<view class="option-item">
				<uni-icons id="option" type="gear" size="25"></uni-icons>
				设置
				<uni-icons id="option-arrow" type="right"></uni-icons>
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
	page {
		background-color: #f1f1f1;
		height: 100%;
	}
	
	.user-info-container {
		display: flex;
		// justify-content: center;
		align-items: center;
		background-color: #ffffff;
		border-top: 1px solid #aaa;
		border-bottom: 1px solid #aaa;
		margin-bottom: 17px;
	}
	.user-avatar-box {
		position: relative;
		left: 0%;
		border: 1px solid #000;
		border-radius: 5px;
		overflow: hidden;
		width: 88px;
		height: 88px;
		margin: 32px 10px 32px 16px;
		
		#img {
			max-width: 100%;
			max-height: 100%;
			display: block;
			margin: auto;
		}
	}
	
	.user-info-box {
		display: flex;
		flex-direction: column;
		justify-content: center;
		
		.user-name {
			color: #000;
			font-size: 23px;
			font-style: normal;
			font-weight: 400;
			line-height: normal;
			margin-bottom: 18px;
		}
		
		.register-time {
			color: #000;
			font-family: Inter;
			font-size: 13px;
			font-style: normal;
			font-weight: 400;
			line-height: normal;
		}
	}
	
	.user-qrcode-box {
		display: flex;
		justify-content: center;
		align-items: center;
		
		#qrcode {
			width: 25px;
			height: 25px;
			margin-left: 65px;
			margin-right: 5px;
		}
	}
	
	.option-container {
		display: flex;
		flex-direction: column;
		gap: 8px;
		
		.option-item {
			font-size: 15px;
			background-color: #ffffff;
			height: 37px;
			display: flex;
			align-items: center;
			border-top: 1px solid #aaa;
			border-bottom: 1px solid #aaa;
		}
		
		#option{
			margin-right: 22px;
			margin-left: 18px;
		}
		
		#option-arrow {
			position: absolute;
			right: 13px;
		}
	}
</style>
