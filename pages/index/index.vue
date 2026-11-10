<template>
	<view class="contanier">
		
		<Tabs>
			
			<template v-slot:my>
				<text>这是我的界面</text>
			</template>
			
			<template v-slot:music>
				<text>这是音乐馆界面</text>
			</template>
			
			<template v-slot:discover>
				<text>这是发现界面</text>
			</template>
			
		</Tabs>
	</view>
</template>