<template>
	<view class="RepaymentPlan">
		<view class="transfer-title">
			<occupyVue hight="90rpx"></occupyVue>
			<backtaberVue  :TitleImage='TitleImage' :rigthIcon="rigthIcon" IconHeight="45rpx" IconWidth="45rpx" Padding="0 30rpx">
				还款计划
			</backtaberVue>
		</view>
		<view class="prompt">
			<text>注:</text> 本还款计划是按照借款合同约定的定价基准的当前值计算的，请您关注重定价日并重新更新查看还款计划表。
		</view>
		<view class="list">
			<YSteps lineNum='0' color='#fff' backgroundColor='#d7d7d7' :infoList='list'></YSteps>
		</view>
	</view>
</template>

<script>
	import occupyVue from '../../components/occupy.vue'
	import backtaberVue from '../../components/backtaber.vue'
	import YSteps from '@/components/Y-Steps/Y-Steps.vue'
	export default {
		data() {
			return {
				TitleImage:'../../static/ic_black_left_back.png',
				rigthIcon:[{icon:'../../static/info_details_icon_click_more.png'}],
				list: [
				        {
							time: '2025-03-28',
				            date: '2666.50',
				            info: '含本金0.00+利息2666.50',
							SubInfo:'本期还款状态:',
							state:'待还款'
				        },
						{
							time: '2025-04-28',
						    date: '2666.50',
						    info: '含本金0.00+利息2666.50',
							SubInfo:'本期还款状态:',
							state:'待还款'
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
			YSteps
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
	.RepaymentPlan{
		width: 100vw;
		min-height: 100vh;
		background-color: #f8f8f8;
		padding-bottom: 50rpx;
		.transfer-title{
			background-color: #fff;
			position: fixed;
			top: 0;
			z-index: 999;
		}
		.prompt{
			width: 90%;
			margin: 0 auto;
			font-size: 25rpx;
			color: #9788a7;
			margin-top: 170rpx;
			text{
				color: #d89e5b;
			}
		}
		.list{
			width: 90%;
			margin: 0 auto;
			margin-top: 20rpx;
		}
	}
</style>
