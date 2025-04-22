<template>
	<view class="TransferDetalis-Detalis">
		<view class="transfer-title">
			<occupyVue hight="90rpx"></occupyVue>
			<backtaberVue  :TitleImage='TitleImage' :rigthIcon="rigthIcon" IconHeight="45rpx" IconWidth="45rpx" Padding="0 30rpx">
				交易详情
			</backtaberVue>
		</view>
		<view class="TransferDetalis-Detalis-titleBox">
			<span>{{Detali.name}}</span>
			<view class="TitleBox-Money">
				<view class="Tishi" :style="{color: !Detali.IsTure ? '#cb5a31' : '#14b570'}">
					{{!Detali.IsTure ? '收入' : '支出'}}
				</view>
				<span :style="{color: !Detali.IsTure ? '#cb5a31' : '#14b570'}">{{Detali.money}}</span>
			</view>
			<text>余额 ￥{{Detali.balance}}</text>
		</view>
		<view class="TransferDetalis-Detalis-ListView">
			<view class="ListView" v-for="(item,index) in ListView" :key="index" :style="{borderBottom:ListView.length === index+1 ? 'none' : '1px solid #f4f4f4'}">
				<span>{{item.name}}</span>
				<text>{{Detali.arr[index]}}</text>
			</view>
		</view>
		
		<view class="TransferDetalis-Detalis-ListView">
			<view class="ListView" style="border: none;">
				<span>所属账本</span>
				<view>创建账本 <image src="@/static/upsdk_payment_right.webp" mode=""></image> </view>
			</view>
		</view>
	</view>
</template>

<script>
	import occupyVue from '../../components/occupy.vue'
	import backtaberVue from '../../components/backtaber.vue'
	export default {
		data() {
			return {
				TitleImage:'../../static/ic_black_left_back.png',
				rigthIcon:[{icon:'../../static/info_details_icon_click_more.png'}],
				ListView:[
					{name:'交易卡号',SubText:'622663******0436'},
					{name:'交易时间',SubText:'2025-03-21 23:27:14'},
					{name:'币种',SubText:'人民币'},
					{name:'摘要',SubText:'网银跨行汇款转账'},
					{name:'对方账户',SubText:'622588******3781'},
					{name:'交易机构',SubText:'广州琶洲支行'},
				],
				Detali:''
			};
		},
		components:{
			occupyVue,
			backtaberVue
		},
		created() {
			this.Detali = uni.getStorageSync('Detali')
			console.log(this.Detali);
		}
	}
</script>

<style lang="scss">
	.TransferDetalis-Detalis{
		width: 100vw;
		min-height: 100vh;
		background-color: #f8f8f8;
		.transfer-title{
			background-color: #fff;
		}
		.TransferDetalis-Detalis-titleBox{
			width: 95%;
			margin: 0 auto;
			background-color: #fff;
			text-align: center;
			padding: 50rpx 0;
			margin-top: 20rpx;
			border-radius: 10rpx;
			.TitleBox-Money{
				display: flex;
				justify-content: center;
				align-items: center;
				margin: 20rpx auto;
				.Tishi{
					height: 30rpx;
					padding: 0 10rpx;
					margin-top: -10rpx;
					display: flex;
					align-items: center;
					justify-content:center;
					border-radius: 50rpx;
					color: #c48165;
					font-size: 20rpx;
					border: 1px solid;
				}
				span{
					font-size: 45rpx;
					margin-left: 20rpx;
				}
			}
			span{
				font-size: 30rpx;
			}
			text{
				font-size: 25rpx;
				color: #ccc;
			}
		}
		.TransferDetalis-Detalis-ListView{
			width: 95%;
			background-color: #fff;
			margin: 0 auto;
			margin-top: 20rpx;
			border-radius: 20rpx;
			.ListView{
				width: 90%;
				padding: 30rpx 0;
				border-bottom: 1px solid #f4f4f4;
				margin: 0 auto;
				display: flex;
				justify-content: space-between;
				align-items: center;
				span{
					font-size: 30rpx;
				}
				text{
					font-size: 28rpx;
					color: #888;
				}
				view{
					font-size: 28rpx;
					color: #888;
					display: flex;
					align-items: center;
					image{
						width: 40rpx;
						height: 40rpx;
						margin-top: 5rpx;
					}
				}
			}
		}
	}
</style>
