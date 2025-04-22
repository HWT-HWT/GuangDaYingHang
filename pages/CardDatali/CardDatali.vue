<template>
	<view class="CardDatali">
		<view class="Account-title">
			<occupyVue hight="90rpx"></occupyVue>
			<backtaberVue  :TitleImage='TitleImage' :rigthIcon="rigthIcon" @GetIndex='GetIndex'>
				我的账户
			</backtaberVue>
		</view>
		
		<view class="CardDali">
			<view class="CardDali-title">
				<view class="title-box">
					<span>622663******0436</span>
					<image src="@/static/e_card_eye_close.png" mode=""></image>
					<view class="color">
						默认卡
					</view>
				</view>
			</view>
			
			<view class="CardDali-Money">
				<view class="Money-image">
					<image src="@/static/card-bg-1.png" mode=""></image>
					<view class="Money">
						<span @click="NextEye">
							可用余额(元) 
							<image v-if="eye" src="@/static/xwr_wealth_my_wallet_eye_close.png" mode=""></image>
							<image v-else src="@/static/today_hot_talk_eye.png" mode=""></image> 
						</span>
						<text>{{ eye ? '******' :'0.00'}}</text>
					</view>
				</view>
			</view>
			
			<view class="CardDali-Foot">
				<span>开户行:广州琶洲支行</span>
				<image src="@/static/CardDatali-icon-1.png" mode=""></image>
			</view>
		</view>
			
		<view class="CardDatali-payment">
			<view class="payment">
				<span>快捷支付</span>
				<view>
					<image src="@/static/CardDatali-icon-2.png" mode=""></image>
					<image style="width: 10rpx; height: 15rpx;" src="../../static/right_arr2.webp" mode=""></image>
				</view>
			</view>
		</view>
	
		<view class="CardDatali-tabs">
			<view class="Account-tabs">
				  <z-tabs ref="tabs" :list="tabList" :current="current" @change="tabsChange" :bar-style="{background:'#7d38d1'}" :active-style='{color:"#7647b0"}' :tabs-style='{height:"100rpx",borderRadius:"20rpx"}' />
			</view>
			<view class="tabs-Text">
				<view class="Text">
					<span>活期</span>
					<p>人民币</p>
				</view>
				<text>0.00</text>
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
				rigthIcon:[
					{name:'总资产',icon:'../../static/title-icon-3.png'},
					{name:'账户管理',icon:'../../static/title-icon-4.png'}
				],
				eye:true,
				tabList: ['资产组成','最近交易'],
				current: 0,
			};
		},
		components:{
			occupyVue,
			backtaberVue
		},
		methods:{
			NextEye(){
				this.eye = !this.eye
			},
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
		}
	}
</script>

<style lang="scss" scoped>
	.CardDatali{
		width: 100vw;
		height: 100vh;
		font-size: 30rpx;
		background-color: #f8f8f8;
		.Account-title{
			background-color: #fff;
			padding-bottom: 10rpx;
		}
		.CardDali{
			width: 90%;
			margin: 0 auto;
			margin-top: 20rpx;
			border-radius: 20rpx;
			padding-bottom: 20rpx;
			background-color: #fff;
			.CardDali-title{
				padding:30rpx;
				display: flex;
				justify-content: space-between;
				.title-box{
					display: flex;
					align-items: center;
					font-size: 30rpx;
					font-weight: bold;
					image{
						width: 30rpx;
						height: 15rpx;
						margin: 0 10rpx;
					}
					.color{
						display: flex;
						align-items: center;
						padding:5rpx 20rpx;
						margin: 0 10rpx;
						color: #fff;
						border-radius: 20rpx;
						background: linear-gradient(to bottom , #e6a052 , #e41319);
						font-size: 25rpx;
					}
				}
				.SetName{
					color: #888;
					font-size: 25rpx;
					display: flex;
					align-items: center;
					image{
						width: 30rpx;
						height: 30rpx;
						margin-left: 5rpx;
					}
				}
			}
			.CardDali-Money{
				display: flex;
				align-items: center;
				padding:0 30rpx;
				justify-content: space-between;
				.Money-image{
					display: flex;
					align-items: center;
					image{
						width: 180rpx;
						height: 120rpx;
					}
					.Money{
						display: flex;
						margin-left: 20rpx;
						align-items: center;
						flex-wrap: wrap;
						color: #999;
						image{
							width: 30rpx;
							height: 30rpx;
							margin-left: 10rpx;
						}
						text{
							font-weight: bold;
							color: #d35b2d;
							font-size:35rpx;
							width: 100%;
						}
					}
				}
			}
			.CardDali-Foot{
				width: 90%;
				margin: 0 auto;
				display: flex;
				align-items: center;
				font-size: 30rpx;
				justify-content: space-between;
				margin-top: 10rpx;
				image{
					width: 70rpx;
					height: 70rpx;
				}
			}
		}
		.CardDatali-payment{
			width: 90%;
			margin: 0 auto;
			margin-top: 20rpx;
			background-color: #fff;
			border-radius: 20rpx;
			
			.payment{
				display: flex;
				align-items: center;
				justify-content: space-between;
				padding: 30rpx;
				view{
					display: flex;
					align-items: center;
					image{
						width: 50rpx;
						height: 50rpx;
						margin-left: 10rpx;
					}
				}
			}
			
		}
		.CardDatali-tabs{
			width: 90%;
			margin: 0 auto;
			margin-top: 20rpx;
			border-radius: 20rpx;
			background-color: #fff;
			.tabs-Text{
				display: flex;
				// align-items: center;
				justify-content: space-between;
				padding: 30rpx;
				.Text{
					span{
						width: 100%;
						font-size: 35rpx;
					}
					p{
						font-size: 25rpx;
						margin-top: 10rpx;
					}
				}
				text{
					font-size: 32rpx;
					font-weight: bold;
				}
			}
		}
	}
</style>
