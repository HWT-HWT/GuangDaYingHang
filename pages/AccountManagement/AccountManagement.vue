<template>
	<view class="AccountManagement">
		<view class="Account-title">
			<occupyVue hight="90rpx"></occupyVue>
			<backtaberVue  :TitleImage='TitleImage' :rigthIcon="rigthIcon" IconHeight="45rpx" IconWidth="45rpx" Padding="0 30rpx">
				账号管理
			</backtaberVue>
		</view>
		<view class="Account-CardDali">
			<view class="CardDali-Money">
				<view class="Money-image">
					<image src="@/static/card-bg-1.png" mode=""></image>
					<view class="Money">
						<span>622663******0436  </span>
						<view class="label">
							<view class="color">
								默认卡
							</view>
							<view class="color Card">
								借记卡
							</view>
						</view>
						<view class="SetCard">
							<view class="SetCard-box">
								<image src="@/static/AccountManagement-icon-1.png" mode=""></image>
								未命名
							</view>
							<view class="SetCard-box">
								<image src="@/static/AccountManagement-icon-2.png" mode=""></image>
								密码管理
							</view>
						</view>
					</view>
				</view>
			</view>
			<view class="CardDali-btn">
				<view class="btn" v-for="(item,index) in cardBtn" :key="index">
					{{item}}
				</view>
				<image src="@/static/info_details_icon_click_more.png" mode=""></image>
			</view>
		</view>
		<view class="Account-Add">
			<view class="btn">
				+ 添加新卡片
			</view>
		</view>
	</view>
</template>

<script>
	import occupyVue from '../../components/occupy.vue'
	import backtaberVue from '../../components/backtaber.vue'
	export default {
		name:"AccountManagement",
		data() {
			return {
				TitleImage:'../../static/ic_black_left_back.png',
				rigthIcon:[{icon:'../../static/info_details_icon_click_more.png'}],
				cardBtn:['账户挂失','一键锁卡/解锁','设为亲友号'],
				Add:['开通电子账户','添加新卡片']
			};
		},
		components:{
			backtaberVue,
			occupyVue,
		}
	}
</script>

<style lang="scss" scoped>
	.AccountManagement{
		width: 100vw;
		height: 100vh;
		background-color: #f2f2f2;
		.Account-title{
			background-color: #fff;
		}
		.Account-CardDali{
			width: 95%;
			margin: 0 auto;
			background-color: #fff;
			margin-top: 20rpx;
			border-radius: 10rpx;
			.CardDali-Money{
				display: flex;
				align-items: center;
				padding:30rpx;
				justify-content: space-between;
				.Money-image{
					display: flex;
					align-items: center;
					image{
						width: 150rpx;
						height: 100rpx;
					}
					.Money{
						margin-left: 20rpx;
						font-size: 32rpx;
						.label{
							display: flex;
							.color{
								width: 80rpx;
								text-align: center;
								padding:5rpx 20rpx;
								margin:10rpx 0;
								color: #fff;
								border-radius: 20rpx;
								background: linear-gradient(to bottom , #e6a052 , #e41319);
								font-size: 25rpx;
								margin-right: 10rpx;
							}
							.Card{
								background: #fd8d08;
							}
						}
						.SetCard{
							display: flex;
							.SetCard-box{
								display: flex;
								align-items: center;
								font-size: 25rpx;
								margin-right: 80rpx;
								image{
									width: 35rpx;
									height: 35rpx;
								}
							}
						}
					}
				}
			}
			.CardDali-btn{
				padding: 30rpx;
				margin: 0 auto;
				display: flex;
				justify-content: space-between;
				align-items: center;
				border-top: 1px solid #ddd;
				.btn{
					display: flex;
					align-items: center;
					height: 30rpx;
					border-right: 1px solid #ddd;
					padding: 0 20rpx;
					color: #7c47be;
					font-size: 28rpx;
				}
				image{
					width: 40rpx;
					height: 40rpx;
				}
			}
		}
		.Account-Add{
			width: 95%;
			margin: 0 auto;
			display: flex;
			justify-content: space-between;
			.btn{
				flex: 1;
				border: 1px solid;
				padding: 25rpx 0rpx;
				border-radius: 10rpx;
				color: #794da5;
				margin-top: 40rpx;
				display: flex;
				justify-content: center;
				align-items: center;
				font-size: 30rpx;
			}
		}
	}
</style>