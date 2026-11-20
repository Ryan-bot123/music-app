<template>
	<!-- 网格列表 -->
	<view class="grid-list">
		<view class="grid-item" v-for="(item, index) in list" :key="index"
			:style="{ width: (100 / column) + '%' }">
			<!-- 音乐 -->
			<view class="grid-item-box">
				<!-- 2.绑定参数：注意src与name一定要与mock.js中图片地址与音乐名称地址一致 -->
				<image :src="item.src" mode="aspectFill"></image>
				<text class="text">{{ item.name }}</text>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		name: "MusicListComponent",
		data() {
			return {

			};
		},
		// 1.子组件参数定义
		props: {
			column: { //列数
				type: Number,
				required: true
			},
			list: {
				type: Array,
				required: true,
				validator: function(value) { //非必须，若是有自信确保数据正确
					// 1.检查 'value' 是否确实为数组，如果不是则返回 false
					if (!Array.isArray(value)) {
						return false
					};
					// 2.遍历数组中的每个元素，检查它们是否都包含歌曲图片'src' 和 歌曲名称'name' 属性
					for (let i = 0; i < value.length; i++) {
						//3.缺少 歌曲图片'src' 或 歌曲名称'name' 属性，则返回 false
						if (!value[i].src || !value[i].name) return false;
					}
					//4.验证通过
					return true;
				}
			},

		}
	}
</script>

<style lang="scss">
	// 网格列表整体
	.grid-list {
		display: flex;
		flex-direction: row;
		flex-wrap: wrap;
	}

	// 每一项
	.grid-item {
		box-sizing: border-box;
		padding: 0 5rpx;
		margin-bottom: 20rpx;

		.grid-item-box {
			width: 100%;
			height: auto;

			// 图片
			image {
				width: 100%;
				height: 200rpx;
			}
		}
	}
</style>