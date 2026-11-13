<template>
	<view class="container">
		<Tabs>
			<template v-slot:my>
				这是我的页面
			</template>
			<template v-slot:music>
				<MusicTabPage/>
			</template>
			<template v-slot:discover>
				这是发现页面
			</template>
		</Tabs>
	</view>
</template>

<script>
	// 1. 导入组件
	import Tabs from "../../components/Tabs.vue"
	import MusicTabPage from "../../components/MusicTabPage.vue";
	export default {
		// 2. 注册组件
		components: {
			Tabs,
			MusicTabPage
		},
		data() {
			return {
				
			}
		},
		methods: {

		}
	}
</script>

<style>
	.container {
		
	}
</style>
