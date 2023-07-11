<template>
	<view class="body">
		<!-- 标题 -->
		<view class="title">
			身份证注册
		</view>
		<!-- 头像选择 -->
		<view class="avatar-choose">
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
				<input password type="text" v-model="ID" placeholder="填写密码">
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
			<text id="agree" @click="agreeNaviagte">《软件许可及服务协议》</text>
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
				
			};
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
