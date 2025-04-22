<template>
	<view class="Account">
		<view class="Account-title">
			<occupyVue hight="90rpx"></occupyVue>
			<backtaberVue  :TitleImage='TitleImage' :rigthIcon="rigthIcon" @GetIndex='GetIndex'>
				我的账户
			</backtaberVue>
		</view>
		<view class="Account-tabs">
			  <z-tabs ref="tabs" :list="tabList" :current="current" @change="tabsChange" :bar-style="{background:'#7d38d1'}" :active-style='{color:"#7647b0"}' :tabs-style='{height:"100rpx"}' />
		</view>
		<DebitCardVue v-if="current == 0"></DebitCardVue>
		<CreditCardVue v-if="current == 1"></CreditCardVue>
		<OtherCardsVue v-if="current == 2"></OtherCardsVue>
		<FriendCardVue v-if="current == 3"></FriendCardVue>
	</view>
</template>

<script>
	import occupyVue from '../../components/occupy.vue'
	import backtaberVue from '../../components/backtaber.vue'
	import DebitCardVue from '../../components/DebitCard.vue'
	import CreditCardVue from '../../components/CreditCard.vue'
	import OtherCardsVue from '../../components/OtherCards.vue'
	import FriendCardVue from '../../components/FriendCard.vue'
	export default {
		data() {
			return {
				TitleImage:'../../static/ic_black_left_back.png',
				rigthIcon:[
					{name:'总资产',icon:'../../static/title-icon-3.png'},
					{name:'账户管理',icon:'../../static/title-icon-4.png'}
				],
				tabList: ['借记账号','信用卡','他行账号','亲友号'],
				current: 0,
			}
		},
		methods: {
			tabsChange(index){
				this.current = index
			},
			GetIndex(index){
				index === 0 ? uni.navigateTo({
					url:'/pages/property/property'
				}) : ''
				index === 1 ? uni.navigateTo({
					url:'/pages/AccountManagement/AccountManagement'
				}) : ''
			}
		},
		components:{
			backtaberVue,
			occupyVue,
			DebitCardVue,
			CreditCardVue,
			OtherCardsVue,
			FriendCardVue
		}
	}
</script>

<style scoped lang="scss">
	.Account{
		width: 100vw;
		height: 100vh;
		background-color: #f2f2f2;
		.Account-title{
			background-color: #fff;
			.Title{
				display: flex;
				flex-wrap:wrap;
				align-items: center;
				justify-content: space-between;
			}
		}
		
	}
</style>
