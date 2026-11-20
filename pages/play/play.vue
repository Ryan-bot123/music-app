<template>
	<view class="container">
		<!-- 全屏音频背景图片 -->
		<image class="fullscreen-image"
			src="/static/image/bg_img/bg1.jpg"
			mode="aspectFill">
		</image>

		<!-- 中间内容：上一首 / 圆形封面 / 下一首 -->
		<view class="content">
			<!-- 上一首按钮 -->
			<view class="control-button last-music">
				<image src="/static/image/icons/last_music.png" mode="aspectFit"></image>
			</view>

			<!-- 圆形封面 -->
			<image class="cover" src="/static/image/bg_img/bg1.jpg" mode="aspectFill"></image>

			<!-- 下一首按钮 -->
			<view class="control-button next-music">
				<image src="/static/image/icons/next_music.png" mode="aspectFit"></image>
			</view>
		</view>
	</view>
</template>


<script>
	export default {
		data() {
			return {

			}
		},
		methods: {

		}
	}
</script>

<style lang="scss">
.container {
	position: relative;
	width: 100%;
	height: 100vh; //全屏高度
	overflow: hidden;

	.fullscreen-image {
		position: absolute;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		//确保替换元素的内容缩放并保持宽高比，以完全覆盖其框
		object-fit: cover;
		filter: blur(12px); // 模糊效果
	}

	// 中间行：横向排列封面与按钮
	.content {
		position: absolute;
		top: 50%;
		left: 0;
		right: 0;
		transform: translateY(-50%);
		display: flex;
		align-items: center;
		justify-content: center;
	}

	// 圆形封面
	.cover {
		width: 340rpx;
		height: 340rpx;
		border-radius: 50%;
		animation: rotate 20s linear infinite; // 持续旋转
	}

	// 上一首 / 下一首按钮
	.control-button {
		width: 80rpx;
		height: 80rpx;
		border-radius: 50%;
		border: 2rpx solid rgba(255, 255, 255, 0.8);
		background-color: rgba(255, 255, 255, 0.1);
		display: flex;
		align-items: center;
		justify-content: center;

		image {
			width: 45rpx;
			height: 45rpx;
		}
	}

	.last-music {
		margin-right: 40rpx;
	}

	.next-music {
		margin-left: 40rpx;
	}
}

@keyframes rotate {
	from {
		transform: rotate(0deg);
	}

	to {
		transform: rotate(360deg);
	}
}
</style>
