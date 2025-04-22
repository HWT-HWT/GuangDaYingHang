<template>
	<view class="RepaymentDetails">
		<view class="transfer-title">
			<occupyVue hight="90rpx"></occupyVue>
			<backtaberVue  :TitleImage='TitleImage' :rigthIcon="rigthIcon" IconHeight="45rpx" IconWidth="45rpx" Padding="0 30rpx">
				还款明细
			</backtaberVue>
		</view>
		<view class="prompt">
			<titleVue :LFontW="false" RFontSize="30" Lcolor="#727272" RColor="#727272" :icon="true" IconSize="1.2">
				<template #left>
					还款信息
				</template>
				<template #rigth>
					全部还款状态
				</template>
			</titleVue>
		</view>
		<view class="RepaymentDetails-ListView" v-if="false">
			<view class="ListView" v-for="(item,index) in RepaymentDetails" :key="index">
				<span>{{item}}</span>
				<image v-if="index === 0" src="@/static/icon_account_check-1.png" mode=""></image>
			</view>
		</view>
		<view class="list">
			<YSteps lineNum='0' color='#fff' backgroundColor='#7d38d1' :infoList='list' TextTitleColor='#000' SubTextColor='#666' PadingBottom='150rpx' TitleSize='30rpx' TextSize='28rpx'></YSteps>
		</view>
	</view>
</template>

<script>
	import occupyVue from '../../components/occupy.vue'
	import backtaberVue from '../../components/backtaber.vue'
	import YSteps from '@/components/Y-Steps/Y-Steps.vue'
	import titleVue from '../../components/titleVue.vue'
	export default {
		data() {
			return {
				TitleImage:'../../static/ic_black_left_back.png',
				rigthIcon:[{icon:'../../static/info_details_icon_click_more.png'}],
				RepaymentDetails:['全部还款状态','已结清','逾期','取消'],
				list: [
						{
							time: '2025-03-20',
						    date: '2666.50',
						    info: '含本金0.00+利息2666.50',
							SubInfo:'本期还款状态:',
							state:'正常还款'
						},
						{
							time: '2025-02-20',
						    date: '2666.50',
						    info: '含本金0.00+利息2666.50',
							SubInfo:'本期还款状态:',
							state:'正常还款'
						}, 
						{
							time: '2025-01-20',
						    date: '2666.50',
						    info: '含本金0.00+利息2666.50',
							SubInfo:'本期还款状态:',
							state:'正常还款'
						},
						{
							time: '2024-12-20',
						    date: '2666.50',
						    info: '含本金0.00+利息2666.50',
							SubInfo:'本期还款状态:',
							state:'正常还款'
						},
						{
							time: '2024-11-20',
						    date: '2666.50',
						    info: '含本金0.00+利息2666.50',
							SubInfo:'本期还款状态:',
							state:'正常还款'
						},
						{
							time: '2024-10-20',
						    date: '2666.50',
						    info: '含本金0.00+利息2666.50',
							SubInfo:'本期还款状态:',
							state:'正常还款'
						},
						{
							time: '2024-09-20',
						    date: '2666.50',
						    info: '含本金0.00+利息2666.50',
							SubInfo:'本期还款状态:',
							state:'正常还款'
						},
						{
							time: '2024-08-20',
						    date: '2666.50',
						    info: '含本金0.00+利息2666.50',
							SubInfo:'本期还款状态:',
							state:'正常还款'
						},
				    ],
					Zzclist:[
						{id:1,name:'全部',active:false},
						{id:2,name:'代还款',active:false},
						{id:3,name:'已还款',active:false},
						{id:4,name:'欠款',active:false}
					],
					istrue:false,
					titleName:'全部',
					zzcId:''
			};
		},
		components:{
			occupyVue,
			backtaberVue,
			YSteps,
			titleVue
		},
		methods:{
			zzcBtn(id,name){
				this.Zzclist.map(item=>item.active=false)
				this.Zzclist.find(item=>item.id === id).active = !this.Zzclist.find(item=>item.id === id).active
				setTimeout(()=>{
					this.istrue = false
				},200)
				this.titleName = name 
				this.zzcId = id
			},
			zzcIsTrue(){
				this.istrue = !this.istrue
			},
		}
	}
</script>

<style lang="scss">
	.RepaymentDetails{
		width: 100vw;
		background-color: #f8f8f8;
		padding-bottom: 50rpx;
		.transfer-title{
			background-color: #fff;
			position: fixed;
			top: 0;
			z-index: 999;
		}
		.prompt{
			
			background-color: #fff;
			padding: 0 30rpx;
			margin: 0 auto;
			font-size: 25rpx;
			color: #9788a7;
			margin-top: 150rpx;
			text{
				color: #d89e5b;
			}
		}
		.RepaymentDetails-ListView{
			width: 100vw;
			height: 100vh;
			position: absolute;
			top: 0;
			margin-top: 80rpx;
			background-color: rgba(0, 0, 0, .3);
			.ListView{
				background-color: #fff;
				display: flex;
				align-items: center;
				justify-content: space-between;
				padding: 20rpx;
				image{
					width: 30rpx;
					height:30rpx;
				}
			}
		}
		.list{
			margin: 0 auto;
			margin-top: 20rpx;
		}
	}
	
</style>
