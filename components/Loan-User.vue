<template>
	<view class="LoanUser">
		<view class="Loan-Money">
			<view class="Money-box">
				<p>总贷款余额(元)</p>
				<span>1,000,000.00</span>
				<text>总贷款金额:1,000,000.00</text>
			</view>
		</view>
		<view class="Loan-btn">
			<view class="btn" @click="GoUrl(1)">
				<image src="@/static/loan-User-icon-1.png" mode=""></image>
				<text>申请进度</text>
			</view>
			<view class="btn " style="background-color: #fff4e0;"  @click="GoUrl(2)">
				<image src="@/static/loan-User-icon-2.png" mode=""></image>
				<text>我要提款</text>
			</view>
			<view class="btn" style="background-color: #e8f1ff;" @click="GoUrl(3)">
				<image src="@/static/loan-User-icon-3.png" mode=""></image>
				<text>贷款记录</text>
			</view>
		</view>
		<view class="loan-service">
			<titleVue LFontSize="35" Padding="30rpx">
				<template #left>
					贷款服务
				</template>
			</titleVue>
			<ListView width="25%" TextHeight="40rpx" :listTitle="loanService" Pad="20rpx 0" FontSize="25rpx" BgColor="#fff"></ListView>
		</view>
	</view>
</template>

<script>
	import titleVue from './titleVue.vue';
	import ListView from './ListView.vue';
	export default {
		name:"Loan-User",
		data() {
			return {
				loanService:[
					{name:'存量房贷利率调整',icon:'../../static/loan-user-icon-4.png'},
					{name:'变更贷款周期',icon:'../../static/loan-user-icon-5.png'},
					{name:'贷款计算器',icon:'../../static/loan-user-icon-6.png'},
					{name:'个人信用报告',icon:'../../static/loan-user-icon-7.png'},
					{name:'结清证明',icon:'../../static/loan-user-icon-8.png'},
					{name:'小微贷款授权',icon:'../../static/loan-user-icon-9.png'},
					{name:'利息优惠券',icon:'../../static/loan-user-icon-10.png'},
					{name:'用途佐证材料',icon:'../../static/loan-user-icon-11.png'}
				],
			};
		},
		components:{
			titleVue,
			ListView
		},
		methods:{
			GoUrl(index){
				console.log(index);
				index === 1 ? uni.navigateTo({
					url:'/pages/Apply/Apply'
				}) : ''
				index === 2 ? uni.navigateTo({
					url:'/pages/Withdrawal/Withdrawal'
				}) : ''
				index === 3 ? uni.navigateTo({
					url:'/pages/LoanRecords/LoanRecords'
				}) : ''
			}
		}
	}
</script>

<style lang="scss">
	.LoanUser{
		margin-top: 180rpx;
		.Loan-Money{
			width: 95%;
			margin: 0 auto;
			color: #fff;
			background:url('../static/loan-User-1.png') no-repeat;
			background-size: 100% 100%;
			.Money-box{
				width: 100%;
				padding: 20rpx;
				display: flex;
				flex-wrap: wrap;
				justify-content: center;
				text-align: center;
				line-height: 60rpx;
				p{
					font-size: 25rpx;
				}
				span{
					width: 100%;
					font-size: 55rpx;
				}
				text{
					font-size: 25rpx;
				}
			}
		}
		.Loan-btn{
			width: 95%;
			margin: 0 auto;
			margin-top: 20rpx;
			display: flex;
			justify-content: space-between;
			.btn{
				// width: 30%;
				background-color: #ffede9;
				display: flex;
				flex-wrap: wrap;
				justify-content: center;
				align-items: center;
				text-align: center;
				line-height: 55rpx;
				padding: 25rpx ;
				border-radius: 20rpx;
				image{
					width: 60rpx;
					height: 60rpx;
				}
				text{
					width: 100%;
					font-size: 30rpx;
				}
			}
		}
		.loan-service{
			width: 90%;
			margin: 0 auto;
			margin-top: 20rpx;
			border-radius: 20rpx;
		}
	}
</style>