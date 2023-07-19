<template>
	<view>
		<scroll-view scroll-y="true">
			<view class="msg-item" v-for="(item,index) in msg_list" :key="index" @click="msgClickHandler(item)">
				<!-- 消息图标 -->
				<view class="icon-container">
					<uni-icons type="list" size="40px" color="#2782D7"></uni-icons>
				</view>
				<!-- 消息信息 -->
				<view class="msg-container">
					<view class="msg-title">
						您有一条新的待确认授权申请
					</view>
					<view class="msg-detail">
						申请授权方：{{item.company}}
					</view>
				</view>
				<!-- 消息时间 -->
				<view class="date">
					{{item.date}}
				</view>
			</view>
		</scroll-view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				msg_list: [
					{company: '数字广西有限集团',
					status: '未确认',
					date: '2023-06-28 11:03',
					number: 'XXXX-XXXX-XXXX-XX',
					origin: '广西疫情防控一体化数据库',
					usage: '测试测试测试测试测试测试'},
					{company: '数字广西有限集团',
					status: '未确认',
					date: '2023-06-28 11:03',
					number: 'XXXX-XXXX-XXXX-XX',
					origin: '测试测试测试测试测试测试测试测试测试'},
					{company: '数字广西有限集团',
					status: '未确认',
					date: '2023-06-28 11:03',
					number: 'XXXX-XXXX-XXXX-XX',
					origin: '测试测试'}
				],
				msg_num: 0
			};
		},
		methods: {
			// 消息点击事件
			msgClickHandler(item) {
				uni.navigateTo({
					url: '/subpkg/auth_msg_detail/auth_msg_detail?number=' + item.number
				})
			}
		}
	}
</script>

<style lang="scss">
	.msg-item {
		width: 390px;
		height: 80px;
		display: flex;
		align-items: center;
		border-bottom: 1px solid rgba(0, 0, 0, 0.1);
		
		.msg-container {
			margin-left: 5px;
			
			.msg-title {
				color: #000;
				font-size: 15px;
				font-style: normal;
				font-weight: 400;
				line-height: normal;
				margin-bottom: 5px;
			}
			
			.msg-detail {
				color: rgba(0, 0, 0, 0.50);
				font-size: 10px;
				font-style: normal;
				font-weight: 400;
				line-height: normal;
			}
		}
		
		.date {
			color: rgba(0, 0, 0, 0.50);
			font-size: 12px;
			font-weight: 400;
			line-height: normal;
			position: relative;
			right: -30px;
			top: -25px;
		}
	}
</style>
