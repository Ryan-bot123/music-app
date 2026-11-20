<template>
	<view class="container">
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

		<!-- 金刚区 -->
		<view class="grid">
			<view class="grid-item-box" v-for="(item, index) in contentBar" :key="index" @click="goUrl('../video/video')">
				<!-- 自定义图标 -->
				<uni-icons fontFamily="CustomFont" :size="25" color="#fff">{{item.src}}</uni-icons>
				<!-- 文字 -->
				<text class="text">{{item.name}}</text>
			</view>
		</view>

		<!-- 个性电台  1行2列共24个栅格   第1列占据9格，第2列占据15格-->
		<view class="radio-body">
			<uni-row>
				<!-- 第1列：左侧图片 栅格占据9格-->
				<uni-col :span="9">
					<view class="radio-image" @click="goUrl('../play/play')">
						<image :src="content.img"></image>
						<view class="radio-text">
							<uni-icons type="headphones" color="#fff" size="60rpx"></uni-icons>
							<text>{{content.imgTitle}}</text>
						</view>
					</view>
				</uni-col>

				<!-- 第2列：右侧列表  栅格占据15格-->
				<uni-col :span="15" v-for="(item) in content.list">
					<uni-list-item v-bind:title="item.name" v-bind:note="item.disc">
						<template v-slot:footer>
							<image class="slot-image" v-bind:src="item.src" mode="widthFix"></image>
						</template>
					</uni-list-item>
				</uni-col>
			</uni-row>
		</view>

		<!-- 为你推荐 -->
		<uni-section :title="recommend.title" type="circle">
			<MusicListComponent :column="3" :list="recommend.list"></MusicListComponent>
		</uni-section>
		<!-- 最新专辑 -->
		<uni-section :title="newest.title" type="circle">
			<MusicListComponent :column="3" :list="newest.list"></MusicListComponent>
		</uni-section>
		<!-- 独家内容 -->
		<uni-section :title="sole.title" type="circle">
			<MusicListComponent :column="2" :list="sole.list"></MusicListComponent>
		</uni-section>
	</view>
</template>

<script>
	import {
		swiper,
		contentBar,
		content,
		recommend, //为你推荐
		newest, //最新专辑
		sole //独家内容
	} from '../commons/mock.js'
	import MusicListComponent from '@/components/MusicListComponent.vue';
	
	export default {
		name: "MusicTabPage",
		components: {
			MusicListComponent
		},
		data() {
			return {
				swiper,
				contentBar,
				content,
				recommend,
				newest,
				sole
			};
		},
		methods: {
			goUrl(str) {
				uni.navigateTo({
					url: str
				})
			}
		}
	}
</script>

<style lang="scss">
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

	// 引入金刚区字体图标
	@font-face {
		font-family: CustomFont;
		src: url('../static/iconfont.ttf');
	}

	// 金刚区
	.grid {
		//金刚区整体
		display: flex;
		flex-direction: row;
		margin: -30rpx 27rpx 0;
		width: 93%;
		/* 与屏幕保持一定的间隔 */
		position: relative;
		z-index: 10;

		.grid-item-box {
			//每个选项
			flex: 1;
			/* 每个选项平均分宽度 */
			display: flex;
			flex-direction: column; //列排序
			align-items: center; //水平居中
			justify-content: center; //垂直居中
			padding: 30rpx 0;
			background-color: #00b86b;

			.text {
				//文字
				margin-top: 15rpx;
				font-weight: 600;
				color: #fff;
			}
		}
	}

	// 个性电台
	.radio-body {
		margin: 60rpx 20rpx 20rpx;

		.radio-image {
			//第1列
			position: relative;

			image {
				//背景图片
				width: 90%;
				height: 275rpx;
			}

			.radio-text {
				//耳机图标与文字
				position: absolute;
				top: 50%;
				/* 垂直居中 */
				left: 50%;
				/* 水平居中 */
				transform: translate(-60%, -50%); //微调位置
				color: white;
				/* 文字颜色 */
				font-size: 30rpx;
				font-weight: bold;
				text-align: center;

				text {
					//文字
					display: block; //单独占一行
					margin-top: 10rpx;
				}
			}
		}

		.slot-image {
			//第2列图片
			/* #ifndef APP-NVUE */
			display: block;
			/* #endif */
			margin-right: 10px;
			width: 50px;
			height: 50px;
		}
	}
</style>

