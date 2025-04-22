<template>
	<view class="loan">
		<view class="transfer-title">
			<occupyVue hight="90rpx"></occupyVue>
			<backtaberVue  :TitleImage='TitleImage' :rigthIcon="rigthIcon" IconHeight="45rpx" IconWidth="45rpx" Padding="0 30rpx">
				贷款
			</backtaberVue>
		</view>
		
		<loanLoanPageVue v-if="tabs"></loanLoanPageVue>
		
		<LoanUserVue v-else></LoanUserVue>
		
		
		<view class="loan-tabs" >
			<view class="tabs select" v-if="tabs" >
				<image src="@/static/loan-tab-1.png" mode=""></image>
				<span class="tabs-name">贷款</span>
			</view>
			<view class="tabs " v-if="!tabs" @click="NextTab(2)">
				<image src="@/static/loan-tab-3.png" mode=""></image>
				<span class="tabs-name">贷款</span>
			</view>
			<view class="tabs select" v-if="!tabs">
				<image src="@/static/loan-tab-2.png" mode=""></image>
				<span class="tabs-name">我的</span>
			</view>
			<view class="tabs" v-if="tabs" @click="NextTab(1)">
				<image src="@/static/loan-tab-4.png" mode=""></image>
				<span class="tabs-name">我的</span>
			</view>
		</view>
	</view>
</template>

<script>
	import occupyVue from '../../components/occupy.vue'
	import backtaberVue from '../../components/backtaber.vue'
	import titleVue from '../../components/titleVue.vue'
	import ListView from '../../components/ListView.vue'
	import loanLoanPageVue from '../../components/loan-LoanPage.vue'
	import LoanUserVue from '../../components/Loan-User.vue'
	export default {
		data() {
			return {
				TitleImage:'../../static/ic_black_left_back.png',
				rigthIcon:[{icon:'../../static/info_details_icon_click_more.png'}],
				tabs:true,
				loanService:[
					{name:'贷款计算器',icon:'../../static/loan-service-1.png'},
					{name:'个人信用报告',icon:'../../static/loan-service-2.png'},
					{name:'小微贷款授权',icon:'../../static/loan-service-3.png'},
					{name:'配偶授权',icon:'../../static/loan-service-4.png'},
					{name:'无还本续贷',icon:'../../static/loan-service-5.png'}
				]
			};
		},
		components:{
			occupyVue,
			backtaberVue,
			titleVue,
			ListView,
			loanLoanPageVue,
			LoanUserVue
		},
		methods:{
			NextTab(index){
				console.log(index === 1);
				index === 1 ? this.tabs = false : this.tabs = true
			}
		},
		onLoad(Url) {
			Url.tabs == 1 ? this.tabs = false : this.tabs = true
		}
	}
</script>

<style lang="scss" scoped>
	.loan{
		width: 100vw;
		min-height: 100vh;
		padding-bottom: 50rpx;
		background-color: #f8f8f8;
		.transfer-title{
			width: 100vw;
			background-color: #fff;
			position: fixed;
			top: 0;
			z-index: 999;
		}
		.loan-tabs{
			width: 100vw;
			background-color: #fff;
			position: fixed;
			bottom: 0;
			display: flex;
			justify-content: space-evenly;
			background-color: #fff;
			.tabs{
				width: 110rpx;
				height: 110rpx;
				flex-wrap: wrap;
				display: flex;
				justify-content: center;
				align-items: center;
				border-radius: 50%;
				position: relative;
				top:-20rpx;
				
				z-index: 999;
				image{
					margin-top: 20rpx;
					width: 60rpx;
					height: 60rpx;
				}
				.tabs-name{
					width: 100%;
					text-align: center;
					font-size: 28rpx;
				}
			}
			.select{
				background-color: #fff;
				color: #cf6d48;
			}
		}
	}
</style>
