<template>
	<view class="Card">
		<view class="Account-title">
			<occupyVue hight="90rpx"></occupyVue>
			<backtaberVue  :TitleImage='TitleImage' :rigthIcon="rigthIcon" IconHeight="45rpx" IconWidth="45rpx" Padding="0 30rpx">
				存款
			</backtaberVue>
		</view>
		<view class="index-ViewList">
			<ListViewVue :listTitle="listView" :sizi="'65rpx'" :BgColor="'#fff'" :FontSize="'25rpx'" :Pad="'30rpx 10rpx'"></ListViewVue>
		</view>
		
		<view class="index-banner">
			<swiper :indicator-dots="true" :autoplay="true" :interval="3000" :duration="1000">
				<swiper-item v-for="(item,index) in 4" :key="index">
					<image :src="`../../static/home-banner-${index+1}.png`" mode=""></image>
				</swiper-item>
			</swiper>
		</view>
		
		<wealthInvestVue :wealthInvest="wealthInvestOne" fontWeight='bold' FontSize='30rpx' color='#a80000' :icon="false" :url='urlOne' title="通知存款" SubTitle="随时存入,当日起息,支取提前约定"></wealthInvestVue>
		
		<wealthInvestVue :wealthInvest="wealthInvestTow" fontWeight='bold' FontSize='30rpx' color='#a80000' :icon="false" :url='urlOne' title="安逸存" SubTitle="定期存款,保本保息,乐享安逸"></wealthInvestVue>
		
		<wealthInvestVue :wealthInvest="wealthInvestThree" fontWeight='bold' FontSize='30rpx' color='#a80000' :icon="false" :url='urlOne' title="定存包" SubTitle="当日气息,随用随取,假期利息不断档"></wealthInvestVue>
		
		<wealthInvestVue :wealthInvest="wealthInvestFour" fontWeight='bold' FontSize='30rpx' color='#a80000' :icon="false" :url='urlOne' title="大额存单" SubTitle="热销产品,定期发行,存取随需"></wealthInvestVue>
	</view> 
</template>

<script>
	import occupyVue from '../../components/occupy.vue'
	import backtaberVue from '../../components/backtaber.vue'
	import ListViewVue from '../../components/ListView.vue'
	import wealthInvestVue from '../../components/wealth-invest.vue'
	export default {
		data() {
			return {
				TitleImage:'../../static/ic_black_left_back.png',
				rigthIcon:[{icon:'../../static/info_details_icon_click_more.png'}],
				listView:[
					{
						name:'定期存款',
						icon:'../../static/Home-listIcon-1.png'
					},
					{
						name:'大额存单',
						icon:'../../static/Home-listIcon-2.png'
					},
					{
						name:'通知存款',
						icon:'../../static/Home-listIcon-3.png'
					},
					{
						name:'季季存',
						icon:'../../static/Home-listIcon-4.png'
					},
					{
						name:'安存包',
						icon:'../../static/Home-listIcon-5.png'
					},
					{
						name:'定存包',
						icon:'../../static/Home-listIcon-6.png'
					},
					{
						name:'月爱存',
						icon:'../../static/Home-listIcon-7.png'
					},
					{
						name:'安逸存',
						icon:'../../static/Home-listIcon-8.png'
					},
				],
				urlOne:'../../static/bg_function_customize_credit_card_small.png',
				wealthInvestOne:[
					{
						name:"7天通知存款",
						percentage:'0.45%-1%',
						percentageSuhTitle:'年利率',
						datali:'7天起',
						subDatali:['五万元起','人民币'],
					},
					{
						name:"1天通知存款",
						percentage:'0.1%-0.65%',
						percentageSuhTitle:'年利率',
						datali:'1天起',
						subDatali:['五万元起','人民币'],
					},
				],
				wealthInvestTow:[
					{
						percentage:'1.35%-1.7%',
						percentageSuhTitle:'年利率',
						datali:'2年期',
						subDatali:['50元起','今日起息'],
					},
					{
						percentage:'1.3%-1.6%',
						percentageSuhTitle:'年利率',
						datali:'1年期',
						subDatali:['50元起','今日起息'],
					},
				],
				wealthInvestThree:[
					{
						name:'季季存',
						percentage:'0.85%-1.3%',
						percentageSuhTitle:'年利收益率',
						datali:'3年',
						subDatali:['20万元起','今日起息'],
					},
				],
				wealthInvestFour:[
					{
						percentage:'1.35%-1.7%',
						percentageSuhTitle:'年利率',
						datali:'2年期',
						subDatali:['50元起','今日起息'],
					},
					{
						percentage:'1.3%-1.6%',
						percentageSuhTitle:'年利率',
						datali:'1年期',
						subDatali:['50元起','今日起息'],
					},
				]
			}
		},
		methods: {
			
		},
		components:{
			occupyVue,
			backtaberVue,
			ListViewVue,
			wealthInvestVue
		}
	}
</script>

<style scoped lang="scss"> 
	.Card{
		width: 100vw;
		min-height: 100vh;
		background-color: #f7f7f7;
		.Account-title{
			background-color: #fff;
		}
		.index-ViewList{
			width:90%;
			margin: 0 auto;
			margin-top: 20rpx;
		}
		.index-banner{
			width: 90%;
			margin: 0 auto;
			margin-top: 30rpx;
			height: 170rpx;
			swiper{
				width: 100%;
				height: 100%;
				/deep/.uni-swiper-dot{
					width: 5rpx;
					height: 5rpx;
					border-radius: 10rpx;
				}
				/deep/.uni-swiper-dot-active{
					width: 20rpx;
					height: 5rpx;
					border-radius: 10rpx;
					background-color: #753cba;
				}
				swiper-item{
					image{
						width: 100%;
						height: 170rpx;
					}
				}
				
			}
		}
	}
</style>
