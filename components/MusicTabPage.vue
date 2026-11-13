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
	</view>
</template>

<script>
	import {
		swiper
	} from '../commons/mock.js'
	export default {
		name: "MusicTabPage",
		data() {
			return {
				swiper, //注册轮播图数据
			};
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
</style>

