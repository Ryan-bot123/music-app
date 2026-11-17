<template>
	<view class="music-tab-page">
		<!-- 搜索框 -->
		<view class="search-bar">
			<uni-search-bar :focus="true" clearButton="none" cancelButton="none" placeholder="搜索"></uni-search-bar>
		</view>

		<!-- 轮播图 -->
		<swiper class="bannerContent" autoplay circular>
			<swiper-item v-for="(item, index) in swiper.img" :key="index">
				<image :src="item" class="swiperImg"></image>
			</swiper-item>
		</swiper>

		<!-- 金刚区，纯CSS Flex，均分 5 列 -->
		<view class="kingkong-wrap">
			<view class="kingkong-item" v-for="(item, index) in contentBar" :key="index" @click="handleClick(item, index)">
				<view class="grid-item-box">
					<text class="custom-icon">{{ item.src }}</text>
					<text class="text">{{ item.name }}</text>
				</view>
			</view>
		</view>

		<!-- 个性电台 1 行 2 列共 24 个栅格 第 1 列占据 9 格，第 2 列占据 15 格-->
		<view class="radio-body">
			<uni-row>
				<!-- 第1列：左侧图片 栅格占据9格-->
				<uni-col :span="9">
					<view class="radio-image">
						<image :src="content.img"></image>
						<view class="radio-text">
							<uni-icons type="headphones" color="#fff" size="60rpx"></uni-icons>
							<text>{{content.imgTitle}}</text>
						</view>
					</view>
				</uni-col>

				<!-- 第 2 列： 右侧列表 栅格占据 15 格-->
				<uni-col :span="15">
					<uni-list-item v-for="(item, index) in content.list" :key="index" v-bind:title="item.name" v-bind:note="item.disc">
						<template v-slot:footer>
							<image class="slot-image" v-bind:src="item.src" mode="widthFix"></image>
						</template>
					</uni-list-item>
				</uni-col>
			</uni-row>
		</view>
	</view>
</template>

<script>
	import {
		swiper,
		contentBar,
		content
	} from '../commons/mock.js'
	export default {
		name: "MusicTabPage",
		data() {
			return {
				swiper, //注册轮播图数据
				contentBar,
				content
			};
		},
		methods: {
			handleClick(item, index) {
				console.log('点击金刚区：', item, index)
			}
		}
	}
</script>

<style lang="scss" scoped>
/* 自定义字体，和你之前的CustomFont保持一致 */
@font-face {
	font-family: CustomFont;
	src: url("/static/iconfont.ttf");
}
.custom-icon {
	font-family: CustomFont;
	font-size: 25px;
	color: #fff;
}

// 搜索栏
.search-bar {
	width: 100%;
	background-color: #00c273; //搜索栏背景色
}

// 轮播图
.bannerContent {
	width: 100%;
	height: 320rpx;

	.swiperImg {
		width: 100%;
		height: 100%;
	}
}

// 金刚区
.kingkong-wrap {
	display: flex;
	width: 100%;
	background-color: #00b86b;

	.kingkong-item {
		flex: 1;

		.grid-item-box {
			display: flex;
			flex-direction: column;
			align-items: center;
			justify-content: center;
			padding: 30rpx 0;
		}
	}
}
.text {
	margin-top: 15rpx;
	font-weight: 600;
	color: #fff;
	font-size: 24rpx;
}

// 个性推荐
.radio-body {
	margin: 60rpx 20rpx 20rpx;

	.radio-image { //第1列
		position: relative;

		image { //背景图片
			width: 90%;
			height: 275rpx;
		}
	}

	.radio-text { //耳机图标与文字
		position: absolute;
		top: 50%; // 垂直居中
		left: 50%; // 水平居中
		transform: translate(-60%, -50%); //微调位置
		color: white; // 文字颜色
		font-size: 30rpx;
		font-weight: bold;
		text-align: center;

		text { //文字
			display: block; //单独占一行
			margin-top: 10rpx;
		}
	}

	.slot-image { //第2列图片
		display: block;
		margin-right: 10px;
		width: 50px;
		height: 50px;
	}
}
</style>