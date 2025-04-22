<template>
	<view class="property">
		<view class="transfer-title">
			<occupyVue hight="90rpx"></occupyVue>
			<backtaberVue  :TitleImage='TitleImage' :rigthIcon="rigthIcon" IconHeight="35rpx" IconWidth="35rpx" Padding="0 15rpx" @GetIndex='GetIndex'>
				资产
			</backtaberVue>
		</view>
		<view class="property-Money">
			<view class="property-MyProperty" v-for="(item,index) in accountList" :key="index" @click="NextPage(index)">
				
				<view :style="{borderRight: index == 0 ? '1px solid #ddd' : '', width: index === 0 ? '100%' : ''}" :class="{Select : !select == index }">
					<p>{{item.title}}</p>
					<span>{{item.money}}</span>
				</view>
				<view class="tbas" v-show="select == index"></view>
			</view>
		</view>
		<accountMyMoneyVue v-if="select === 0"></accountMyMoneyVue>
		<accountLoanVue v-else></accountLoanVue>
	</view>
</template>

<script>
	import occupyVue from '../../components/occupy.vue'
	import backtaberVue from '../../components/backtaber.vue'
	import accountMyMoneyVue from '../../components/account-MyMoney.vue';
	import accountLoanVue from '../../components/account-loan.vue';
	export default {
		data() {
			return {
				TitleImage:'../../static/ic_black_left_back.png',
				rigthIcon:[{icon:'../../static/title-icon-6.png',name:'我的账户'},{icon:'../../static/info_details_icon_click_more.png'}],
				select:0,
				accountList:[
					{title:'我的资产(元)',money:'0.00'},
					{title:'我的借款(元)',money:'1,000,000.00'},
				]
			};
		},
		components:{
			occupyVue,
			backtaberVue,
			accountMyMoneyVue,
			accountLoanVue
		},
		methods:{
			NextPage(index){
				console.log(index);
				this.select = index
				console.log(this.select);
			},
			GetIndex(index){
				index === 0 ? uni.navigateTo({
					url:'/pages/Account/Account'
				}) : ''
			}
		},
		onLoad(Url) {
			console.log(Url.id);
			this.select = Url.id || 0
		}
	}
</script>

<style lang="scss">
	.property{
		width: 100vw;
		height: 100vh;
		background-color: #f8f8f8;
		.transfer-title{
			background-color: #fff;
			position: fixed;
			top: 0;
			z-index: 999;
		}
		.property-Money{
			width: 100vw;
			background-color: #fff;
			display: flex;
			margin-top: 160rpx;
			.property-MyProperty{
				width: 50%;
				display: flex;
				flex-wrap: wrap;
				text-align: center;
				justify-content: center;
				padding: 20rpx 0;
				line-height: 45rpx;
				.Select{
					color: #888; 
				}
				view{
					width: 100%;
					p{
						font-size: 30rpx;
					}
					span{
						width: 100%;
						font-size: 35rpx;
					}
				}
				.tbas{
					position: relative;
					top: 20rpx;
					width: 50rpx;
					height: 10rpx;
					border-radius: 20rpx;
					background-color: #7d38d1;
				}
			}
		}
		
	}
</style>
