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
			width: 326px;
			height: 210px;
			border-radius: 15px;
			border: 1px solid #888;
			background: #F1F1F1;
			
			.box-title-item {
				display: block;
				position: absolute;
				margin: 19px 266px 167px 20px;
				color: #000;
				font-size: 20px;
				font-style: normal;
				font-weight: 400;
				line-height: normal;
			}
			
			.acctoun-container {
				display: flex;
				flex-direction: column;
				gap: 7px;
				position: absolute;
				margin: 62px 36px 93px 20px;
			}
		}
	}
</style>
