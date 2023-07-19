<template>
	<view>
		<!-- 此处代码仅作为最终效果展示，并不代表最终业务代码 -->
		<!-- 单条消息工单号已通过url地址传入本页 -->
		<view class="body">
			<!-- 此条授权申请工单号为：{{number}} -->
			<!-- 图标 -->
			<view class="icon-container">
				<uni-icons type="checkbox" size="40"></uni-icons>
			</view>
			<!-- 标题 -->
			<view class="title-container">
				<view class="title">
					个人数据授权确认
				</view>
				<view class="sub-title">
					数字广西有限集团
				</view>
			</view>
			<!-- 详情信息 -->
			<view class="detail-container">
				<view class="left-box">
					<view>当前状态</view>
					<view>申请时间</view>
					<view>数据来源</view>
					<view>工单号</view>
					<view>使用用途</view>
					<view>授权方式</view>
				</view>
				<view class="right-box">
					<view>未确认</view>
					<view>2023-06-28 11:03</view>
					<view>广西疫情防控一体化数据库</view>
					<view>0000-0000-0000-01</view>
					<view>测试测试测试测试测试测试</view>
					<view>线上远程授权</view>
				</view>
			</view>
		</view>
		
		<view class="option-container">
			<view>确认</view>
			<view>拒绝</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				// 授权消息工单号
				number: null
			};
		},
		onLoad:function(option){
			this.number = option.number
			console.log(option.number);
		}
	}
</script>

<style lang="scss">

</style>
