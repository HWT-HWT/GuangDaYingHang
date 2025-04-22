<template>
	<view class="MyLoan">
		<view class="transfer-title">
			<occupyVue hight="90rpx"></occupyVue>
			<backtaberVue  :TitleImage='TitleImage' :rigthIcon="rigthIcon" IconHeight="45rpx" IconWidth="45rpx" Padding="0 30rpx">
				我的贷款
			</backtaberVue>
		</view>
		<view class="PromissoryNote-ListView" style="margin-top: 150rpx;">
			<ListViewBoxVue v-for="(item,index) in MyLoanTitle" :key="index"
			:BorderBottom="index === ContractDetailsListView.length-1 ? false : true"
			:copy='item.copy'
			:icon='item.icon'
			Rcolor="#000"
			>
				<template #name>
					{{item.name}}
				</template>
				<template #right>
					{{item.text}}
				</template>
			</ListViewBoxVue>
			<view class="ListView-Title">
				注:根据我行定价策略，贷款年利率由最新贷款市场报价利率3.95%-75BPs组成;1BP=0.01%。
			</view>
		</view>
		
		<view class="PromissoryNote-ListView">
			<ListViewBoxVue v-for="(item,index) in ContractDetailsListView" :key="index"
			:BorderBottom="index === ContractDetailsListView.length-1 ? false : true"
			:copy='item.copy'
			:icon='item.icon'
			Rcolor="#000"
			>
				<template #name>
					{{item.name}}
				</template>
				<template #right>
					{{item.text}}
				</template>
			</ListViewBoxVue>
		</view>
	</view>
</template>

<script>
	import occupyVue from '../../components/occupy.vue'
	import backtaberVue from '../../components/backtaber.vue'
	import ListViewBoxVue from '../../components/ListView-box.vue'
	export default {
		data() {
			return {
				TitleImage:'../../static/ic_black_left_back.png',
				rigthIcon:[{icon:'../../static/info_details_icon_click_more.png'}],
				MyLoanTitle:[
					{name:'产品名称',text:'助业房抵快贷(循)'},
					{name:'贷款年利率',text:'3.2%'},

				],
				ContractDetailsListView:[
					{name:'借据编号',text:'388824770001RH001'},
					{name:'合同编号',text:'388824770001RH'},
					{name:'贷款期限 ',text:'36个月'},
					{name:'放款日期 ',text:'2024年07月30日'},
					{name:'到期日期',text:'2027年07月30日'},
					{name:'首次还款日',text:'2024年08月20日'},
					{name:'贷款金额(元)',text:'1,000,000.00'},
					{name:'贷款余额(元)',text:'1,000,000.00'},
					{name:'贷款发放支行',text:'广州分行本部'},
					{name:'还款账号',text:'622663******0436'},
					{name:'还款方式',text:'先整息后本息'},
					{name:'还款日期',text:'每月20日'},
					{name:'贷款状态',text:'正常'},
					{name:'下次调息日',text:'2025年7月30日'}
				],
			}
		},
		methods: {
			
		},
		components:{
			occupyVue,
			backtaberVue,
			ListViewBoxVue
		},
	}
</script>

<style scoped lang="scss">
	.MyLoan{
		width: 100vw;
		height: 100vh;
		background-color: #f8f8f8;
		.transfer-title{
			background-color: #fff;
			position: fixed;
			top: 0;
			z-index: 999;
		}
		.PromissoryNote-ListView{
			margin-top: 20rpx;
			background-color: #fff;
			.ListView-Title{
				padding: 20rpx;
				font-size: 30rpx;
				color: #e69433;
			}
		}
	}
</style>
