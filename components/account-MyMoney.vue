<template>
	<view>
		<view class="property-pie">
			<view class="pie-Chart"></view>
			<view class="property-box">
				<view class="Text">
					<span class="percentage">100.00%</span>
					<view class="SubText">
						<view class="box"></view>
						<span>现金</span>
					</view>
				</view>
				
				<view class="Text">
					<span class="percentage">0.00%</span>
					<view class="SubText">
						<view class="box" style="background-color: #fd8b07;"></view>
						<span>投资</span>
					</view>
				</view>
			</view>
		</view>
		<view class="index-notice">
			<view class="notice-text">
				<image src="@/static/bg_qiezi.png" mode=""></image>
			</view>
			<p>近1年年化收益率均值超4%!这类…</p>
			<image src="@/static/upsdk_payment_right.webp" mode=""></image>
		</view>
		<view class="OtherCards-tisi">
			<p>温馨提示:</p>
			<span>1.总资产信息包含相应账户中的冻结资金及控制资金，仅供参考，请以实际信息为准。<br />
				  2.外币资产金额将折算为人民币统计，因汇率实时变动，请以实际信息为准。<br />
				  3.资产信息统计范围包括:现金:活期存款、定存宝(含季季存)、光爱存。 投资:理财、基金/集合计划、私募、定期存款安逸存、大额存单、安存宝、国债。保障:保险、年金、个人养老金、养老保障、商业养老金。<br />
				  4.保险资产因系统时差原因，保单相关信息仅做参考，具体内容以保险公司为准。
			</span>
		</view>
	</view>
</template>

<script>
	export default {
		name:"account-MyMoney",
		data() {
			return {
				
			};
		}
	}
</script>

<style lang="scss" scoped>
	.property-pie{
		width: 95%;
		margin: 0 auto;
		background-color: #fff;
		margin-top: 20rpx;
		padding: 30rpx 0;
		border-radius:20rpx;
		.pie-Chart{
			width: 80px;
			height: 80px;
			border: 25px solid #d8d8d8;
			border-radius: 50%;
			margin: 0 auto;
		}
		.property-box{
			width: 100%;
			display: flex;
			justify-content: center;
			margin-top: 20rpx;
			.Text{
				text-align: center;
				padding:20rpx 50rpx;
				.percentage{
					font-size: 30rpx;
				}
				.SubText{
					display: flex;
					align-items: center;
					justify-content: center;
					.box{
						width: 15rpx;
						height: 15rpx;
						background-color: #d55a2f;
						margin: 0 10rpx;
						border-radius: 5rpx;
					}
					span{
						font-size: 23rpx;
					}
				}
			}
		}
	}
	.index-notice{
		width: 95%;
		margin: 0 auto;
		display: flex;
		justify-content: space-evenly;
		align-items: center;
		padding: 20rpx 0;
		background-color: #fff;
		margin-top: 30rpx;
		border-radius: 20rpx;
		.notice-text{
			padding:0 20rpx;
			display: flex;
			align-items: center;
			image{
				width: 60rpx;
				height: 50rpx;
			}
			font-size: 30rpx;
		}
		p{
			flex: 1;
			font-size: 28rpx;
			color: #555;
		}
		image{
			padding:0 20rpx;
			width: 40rpx;
			height: 40rpx;
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
</style>