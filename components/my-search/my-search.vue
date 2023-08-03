<template>
	<!-- 自定义搜索组件 -->
	<view class="body">
		<!-- 搜索方式选择器 -->
		<view class="selector">
			<picker mode="selector" :range="select_list" @change="changeHandler">
				<view>{{select_item}}</view>
			</picker>
		</view>
		<!-- 搜索框 -->
		<view class="search-box">
			<uni-search-bar radius="16" placeholder="搜索" @focus="focusHandler" @cancel="cancelHandler" @confirm="confirmHandler" v-model="search_value"></uni-search-bar>
		</view>
	</view>
	<!-- 搜索历史区 -->
	<view v-if="history_flag" calss="history">
		<view class="history-title">
			<text>搜索历史</text>
			<uni-icons type="trash" size="20"></uni-icons>
		</view>
		<view class="history-list">
			<uni-tag :text="item" v-for="(item,index) in historys" :key="index"></uni-tag>
		</view>
	</view>
</template>

<script>
	export default {
		name: "my-search",
		data() {
			return {
				select_list: ["企业", "工单号"],
				select_item: "企业",
				// 搜索历史是否显示flag
				history_flag: false,
				// 搜索历史列表
				history_data: ["数字广西有限集团", "中国-东盟信息港股份有限公司", "中国移动广西集团"],
				// 搜索框输入字符串
				search_value: ""
			};
		},
		methods: {
			// 选择列表变化事件
			changeHandler(e) {
				this.select_item = this.select_list[e.detail.value]
				console.log(this.select_item);
			},
			// 搜索栏聚焦事件
			focusHandler() {
				this.setHistoryStatus(true)
			},
			// 搜索栏失去焦点事件
			cancelHandler() {
				this.setHistoryStatus(false)
			},
			// 搜索事件
			confirmHandler() {
				console.log(this.search_value);
				uni.navigateTo({
					url: '/subpkg/log_list/log_list'
				})
			},
			// 搜索历史状态修改
			setHistoryStatus(status) {
				this.history_flag = status
			}
		},
		computed: {
			historys() {
				return [...this.history_data].reverse()
			}
		}
	}
</script>

<style lang="scss">
	.body {
		display: flex;
		align-items: center;
		background-color: #fff;

		.search-box {
			flex: 1;
		}

		.selector {
			display: flex;
			justify-content: center;
			align-items: center;
			width: 79px;
			height: 36px;
			border: 1px solid rgba(0, 0, 0, 0.10);
			border-radius: 20px;
		}
	}

	.history-title {
		display: flex;
		justify-content: space-between;
		align-items: center;
		height: 40px;
		
		font-size: 13px;
		border-bottom: #efefef;
	}
	
	.history-list {
		display: flex;
		flex-wrap: wrap;
		
		.uni-tag {
			margin-top: 5px;
			margin-right: 5px;
		}
	}
</style>