<template>
	<view class="AccountLoan">
		<view class="property-pie">
			<view class="pie-Chart"></view>
			<view class="property-box">
				<view class="Text">
					<span class="percentage">100.00%</span>
					<view class="SubText">
						<view class="box"></view>
						<span>个人贷款</span>
					</view>
				</view>
				
				<view class="Text">
					<span class="percentage">0.00%</span>
					<view class="SubText">
						<view class="box" style="background-color: #7e39cd;"></view>
						<span>信用卡</span>
					</view>
				</view>
			</view>
		</view>
		<view class="index-notice">
			<view class="notice-text">
				<image src="@/static/bg_qiezi.png" mode=""></image>
			</view>
			<p>【财经晚报】-夜涨11元/克!金价…</p>
			<image src="@/static/upsdk_payment_right.webp" mode=""></image>
		</view>
		
		<view class="AccountLoan-User-Loan">
			<titleVue LFontSize="34" :LFontW="false" Lcolor="#4a606d" RColor="#4c6672">
				<template #left>
					个人贷款
				</template>
				<template #rigth>
					1,000,000.00
				</template>
			</titleVue>
			
			<view class="User-Loan-box" @click="GoLoan">
				<span>自营类贷款</span>
				<text>1,000,000.00</text>
			</view>
		</view>
		<view class="AccountLoan-Card">
			<titleVue Lcolor="#9567b6" :LFontW="false" LFontSize="34" RColor="#7542a8">
				<template #left>
					信用卡
				</template>
				<template #rigth>
					0.00
				</template>
			</titleVue>
			<view class="User-Card">
				<view class="Card-image">
					<view class="image"> <image src="@/static/User-card-icon-5.png" mode=""></image> <span>信用卡</span> </view>
					<p>新客办卡,享诸多权益</p>
				</view>
				<view class="btn">
					立即申请
				</view>
			</view>
		</view>
		<view class="OtherCards-tisi">
			<p>温馨提示:</p>
			<span>
				1.总借款信息仅供参考，请以实际信息为准。<br />
				2.借款统计范围为光大银行自营贷款及信用卡欠款。<br />
				3.外币借款金额将折算为人民币统计，因汇率实时变动，请以实际信息为准。<br />
				4.信用卡欠款当前仅汇总统计您名下全部共享额度卡片(含未加挂手机银行的卡片)的账户总欠款金额(不含溢缴款金额)不包括非共享额度特殊卡片的欠款。账户总欠款金额由全部尚未还清的消费、取现、分期已结转、分期未结转本金及息费欠款构成。剩余应还汇总统计您名下全部共享额度卡片(含未加挂手机银行的卡片)的本期账单剩余应还金额，区分币种展示。
			</span>
		</view>
	</view>
</template>

<script>
	import titleVue from './titleVue.vue';
	export default {
		name:"account-loan",
		data() {
			return {
				
			};
		},
		components:{
			titleVue
		},
		methods:{
			GoLoan(){
				uni.navigateTo({
					url:'/pages/loan/loan?tabs=1'
				})
			}
		}
		
	}
</script>

<style lang="scss" scoped>
	.AccountLoan{
		width: 100vw;
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
				border: 25px solid #356277;
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
							background-color: #376172;
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
		.AccountLoan-User-Loan{
			width: 90%;
			margin: 0 auto;
			margin-top: 20rpx;
			.User-Loan-box{
				background-color: #fff;
				padding: 30rpx;
				border-radius: 20rpx;
				display: flex;
				justify-content: space-between;
			}
		}
		.AccountLoan-Card{
			width: 90%;
			margin: 0 auto;
			.User-Card{
				width: 100%;
				margin: 0 auto;
				background-color: #fff;
				display: flex;
				align-items: center;
				margin-top: 20rpx;
				border-radius: 20rpx;
				justify-content: space-between;
				.Card-image{
					display: flex;
					flex-wrap: wrap;
					align-items: center;
					padding: 20rpx;
					.image{
						width: 100%;
						display: flex;
						align-items: center;
						font-size: 30rpx;
						image{
							width: 60rpx;
							height: 50rpx;
						}
					}
					p{
						width: 100%;
						font-size: 22rpx;
						margin-top: 5rpx;
					}
				}
				.btn{
					padding: 10rpx 15rpx;
					border-radius: 50rpx;
					font-size: 25rpx;
					border: 1px solid ;
					color: #c7876e;
					margin-right: 40rpx;
				}
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