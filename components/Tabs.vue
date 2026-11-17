<template>
	<view class="top">
		<view class="bar">
			<view class="tab-item" v-for="(item, index) in tabs" :key="index" :class="{active: item.name===currentTab}"
				@click="switchTab(item.name)">
				{{item.title}}
			</view>
		</view>

		<!-- 三个具名插槽，小程序端按当前 tab 条件渲染 -->
		<view v-if="currentTab==='my'">
			<slot name="my"></slot>
		</view>
		<view v-if="currentTab==='music'">
			<slot name="music"></slot>
		</view>
		<view v-if="currentTab==='discover'">
			<slot name="discover"></slot>
		</view>
	</view>
</template>
<script>
	export default {
		name: "Tabs",
		data() {
			return {
				tabs: [{
						name: 'my',
						title: '我的'
					},
					{
						name: 'music',
						title: '音乐馆'
					},
					{
						name: 'discover',
						title: '发现'
					}
				],
				//当前选中的Tab
				currentTab: 'my'
			};
		},
		methods: {
			switchTab(tabName) {
				this.currentTab = tabName;
			}
		}

	}
</script>

<style lang="scss" scoped>
	.top {
		width: 100%;
		box-sizing: border-box; //确保宽度是100%	
		font-size: 32rpx;

		.bar {
			//菜单导航
			display: flex;
			justify-content: center;
			line-height: 100rpx;
			background-color: #00c273;
			color: #fff;
			height: 10vh;

			.tab-item {
				// tab文字之间的间距
				margin: 0 10rpx;
			}

			// Tab菜单激活效果
			.active {
				color: black;
				font-size: 45rpx;
				font-weight: bold;
			}
		}
	}
</style>