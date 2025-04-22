<template>
	<view class="CreditCard">
		<view class="CreditCard-notice">
			<view class="notice-text">
				<image src="@/static/bg_qiezi.png" mode=""></image>
			</view>
			<p>手机里的中奖“陷阱”</p>
			<image src="@/static/upsdk_payment_right.webp" mode=""></image>
		</view>
		
		<view class="CreditCard-image">
			<image src="@/static/Account-bg-1.png" mode=""></image>
		</view>
		
		<view class="Account-Add">
			<view class="btn">
				+ 添加新卡片
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		name:"CreditCard",
		data() {
			return {
				
			};
		}
	}
</script>

<style lang="scss" scoped>
	.CreditCard{
		width: 100%;
		.CreditCard-notice{
			width: 95%;
			margin: 0 auto;
			display: flex;
			justify-content: space-evenly;
			align-items: center;
			padding: 20rpx 0;	
			background-color: #fff;
			margin-top: 30rpx;
			border-radius: 10rpx;
			.notice-text{
				display: flex;
				align-items: center;
				image{
					width: 70rpx;
					height: 60rpx;
				}
			}
			p{
				
				font-size: 28rpx;
				width: 70%;
				color: #555;
			}
			image{
				width: 40rpx;
				height: 40rpx;
			}
		}
		.CreditCard-image{
			display: flex;
			align-items: center;
			justify-content: center;
			margin-top: 100rpx;
			image{
				width: 500rpx;
				height: 440rpx;
			}
		}
		.Account-Add{
			width: 90%;
			margin: 0 auto;
			display: flex;
			justify-content: space-between;
			.btn{
				flex: 1;
				border: 1px solid;
				padding: 20rpx 0rpx;
				border-radius: 50rpx;
				color: #794da5;
				margin-top: 40rpx;
				display: flex;
				justify-content: center;
				align-items: center;
				font-size: 35rpx;
			}
		}
	}
</style>