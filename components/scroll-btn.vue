<template>
	<view>
		<view class="scroll-view">
			<view class="Optimal-title-btn">
				<view class="Optimal-btn" v-for="(item,index) in list" :key="index">
					{{item}}
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		name:"scroll-btn",
		data() {
			return {
				
			};
		},
		props:{
			list:{
				type:Array
			}
		}
	}
</script>

<style lang="scss" scoped>
	.scroll-view{
		width: 100%;
		margin: 30rpx auto;
		display: flex;
		justify-content: space-between;
		.Optimal-title-btn{
			width: 100%;
			padding-left: 10rpx;
			display: flex;
			align-items: center;
			justify-content: space-between;
			.Optimal-btn{
				height: 45rpx;
				padding: 0 30rpx;
				border-radius: 40rpx;
				font-size: 23rpx;
				background-color: #f8f8f8;
				color: #333;
				display: flex; 	
				align-items: center;
			}
			.Optimal-btn:hover{
				color: #8e60c5;
				background-color: #f2ecfa;
			}
		}
	}
</style>