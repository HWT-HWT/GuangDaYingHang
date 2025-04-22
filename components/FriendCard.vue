<template>
	<view class="FriendCard">
		<view class="CreditCard-image">
			<image src="@/static/Account-bg-1.png" mode=""></image>
		</view>
		<view class="FriendCard-text">
			<p>您名下尚无受托管理的光大亲友账户记录</p>
			<view>亲友号如何添加?一图秒懂亲友号 <image src="../static/purple_right.png" mode=""></image> </view>
		</view>
	</view>
</template>

<script>
	export default {
		name:"FriendCard",
		data() {
			return {
				
			};
		}
	}
</script>

<style lang="scss" scoped>
	.FriendCard{
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
		.FriendCard-text{
			width: 90%;
			margin: 0 auto;
			text-align: center;
			line-height: 50rpx;
			p{
				font-size: 30rpx;
				color: #555;
				font-weight: bold;
			}
			view{
				color: #7b53ac;
				font-size: 28rpx;
				display: flex;
				align-items: center;
				justify-content: center;
				image{
					width: 25rpx;
					margin-left: 15rpx;
					height: 25rpx;
				}
			}
		}
	}
</style>