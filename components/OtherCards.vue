<template>
	<view class="OtherCards">
		<view class="CreditCard-image">
			<image src="@/static/Account-bg-1.png" mode=""></image>
		</view>
		
		<view class="Account-Add">
			<view class="btn">
				+ 添加新卡片
			</view>
		</view>
		
		<view class="OtherCards-tisi">
			<p>温馨提示:</p>
			<span>他行账户签约跨行支付，可在手机银行部分生活场景使用。</span>
		</view>
	</view>
</template>

<script>
	export default {
		name:"OtherCards",
		data() {
			return {
				
			};
		}
	}
</script>

<style lang="scss">
	.OtherCards{
		width: 100%;
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
		.OtherCards-tisi{
			width: 90%;
			margin: 0 auto;
			margin-top: 50rpx;
			p{
				color: #fd8d0a;
				font-weight: bold;
			}
			span{
				font-size: 25rpx;
				color: #888;
			}
		}
	}
</style>