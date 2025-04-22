<template>
	<view class="occupy" :style="{'height':hight}">
		
	</view>
</template>

<script>
	export default {
		name:"occupy",
		data() {
			return {
				
			};
		},
		props:{
			hight:{
				type:[String,Number]
			}
		}
	}
</script>

<style lang="scss" scoped>
	.occupy{
		width: 100%;
	}
</style>