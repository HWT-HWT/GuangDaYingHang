<template>
	<view class="transfer">
		<view class="transfer-title">
			<occupyVue hight="90rpx"></occupyVue>
			<backtaberVue  :TitleImage='TitleImage' :rigthIcon="rigthIcon" IconHeight="45rpx" IconWidth="45rpx" Padding="0 30rpx">
				转账
			</backtaberVue>
		</view>
		<view class="transfer-ListView">
			<view class="ListView" v-for="(item,index) in transferListView" :key="index" :style="{borderRight: !index+1 === transferListView.length ? '1px solid #fff' : 'none'  }" @click="GoUrl(index)">
				<image :src="item.icon" mode=""></image>
				<p>{{item.name}}</p>
			</view>
		</view>
		<view class="transfer-btn">
			<view class="btn" v-for="(item,index) in cardBtn" :key="index"  :style="{border:index+1 === cardBtn.length ?  'none':'1px soilid #ddd'}" @click="GetIndex(index)">
				<image :src="`../../static/transfer-icon-${index+3}.png`" mode=""></image> {{item}}
			</view>
			<view class="CardDali-icon">
				<image src="@/static/upsdk_card_arrow_right.webp" mode=""></image>
			</view>
		</view>
		<view class="transfer-recently">
			<titleVue LFontSize="35" Padding="20rpx 40rpx">
				<template #left>
					最近收款人
				</template>
			</titleVue>
			<view class="recently-ListView">
				您尚未转账，暂无可展示的收款人
			</view>
		</view>
	</view>
</template>

<script>
	import occupyVue from '../../components/occupy.vue'
	import backtaberVue from '../../components/backtaber.vue'
	import titleVue from '../../components/titleVue.vue'
	export default {
		data() {
			return {
				TitleImage:'../../static/ic_black_left_back.png',
				rigthIcon:[{icon:'../../static/info_details_icon_click_more.png'}],
				transferListView:[
					{name:'账号转账',icon:'../../static/transfer-icon-1.png'},
					{name:'手机号转账',icon:'../../static/transfer-icon-2.png'},
				],
				cardBtn:['转账明细','限额设置','绑定手机号'],
			};
		},
		components:{
			backtaberVue,
			occupyVue,
			titleVue
		},
		methods:{
			GoUrl(index){
				console.log(index);
				index === 0 ? uni.navigateTo({
					url:'/pages/remittance/remittance'
				}) : ''
				index === 1 ? uni.navigateTo({
					url:'/pages/RemittancePhone/RemittancePhone'
				}) : ''
			},
			GetIndex(index){
				console.log(index);
				index === 0 ? uni.navigateTo({
					url:'/pages/TransferDetails/TransferDetails'
				}) : ''
			}
		}
	}
</script>

<style lang="scss">
	.transfer{
		width: 100vw;
		height: 100vh;
		background-color: #eeeff3;
		.transfer-title{
			background-color: #fff;
		}
		.transfer-ListView{
			width: 95%;
			margin: 0 auto;
			border-radius: 20rpx 20rpx 0 0;
			background: #8501ad;
			display: flex;
			align-items: center;
			margin-top:20rpx;
			padding: 40rpx 0;
			.ListView{
				flex: 1;
				display: flex;
				flex-wrap: wrap;	
				justify-content: center;
				border-right: 1px solid #fff;
				image{
					width: 100rpx;
					height: 100rpx;
				}
				p{
					margin-top: 10rpx;
					text-align: center;
					color: #fff;
					font-size: 35rpx;
					width: 100%;
				}
			}
		}
		.transfer-btn{
			width: 95%;
			margin: 0 auto;
			padding: 20rpx 0;
			display: flex;
			flex-wrap: wrap;
			justify-content: space-between;
			border-radius: 0 0 20rpx 20rpx;
			align-items: center;
			background-color: #fff;
			.btn{
				flex: 1;
				justify-content: center;
				display: flex;
				align-items: center;
				height: 30rpx;
				border-right: 1px solid #ddd;
				padding: 0rpx 30rpx;
				color: #7c47be;
				font-size: 28rpx;
				margin-top: 10rpx;
				image{
					width: 35rpx;
					height: 35rpx;
					margin-left:5rpx;
				}
			}
			.CardDali-icon{
				width: 100%;
				display: flex;
				justify-content: center;
				align-items: center;
				margin-top: 20rpx;
				image{
					border-radius: 20rpx;
					width: 35rpx;
					height: 35rpx;
				}
			}
		}
		.transfer-recently{
			width: 95%;
			margin: 0 auto;
			background-color: #fff;
			border-radius: 20rpx 20rpx 0 0;
			margin-top: 20rpx;
			
			.recently-ListView{
				background-color: #f8f8f8;
				padding: 40rpx 0rpx 10rpx 0rpx;
				color: #666;
				text-align: center;
				font-size: 32rpx;
				border-top: 1px solid #eaeaea;
			}
		}
	}
</style>
