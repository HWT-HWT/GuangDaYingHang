<template>
	<view>
		<view class="Account-CardDali">
			<view class="CardDali-title">
				<view class="title-box">
					<span>622663******0436</span>
					<image src="@/static/e_card_eye_close.png" mode=""></image>
					<text>I类</text>
					<view class="color">
						默认卡
					</view>
				</view>
				<view class="SetName">
					设置别名 <image src="@/static/card-icon-1.png" mode=""></image>
				</view>
			</view>
			<view class="CardDali-Money">
				<view class="Money-image">
					<image src="@/static/card-bg-1.png" mode=""></image>
					<view class="Money">
						<span @click="NextEye">
							可用余额(元) 
							<image v-if="eye" src="@/static/e_card_eye_close.png" mode=""></image>
							<image v-else src="@/static/e_card_eye_open.png" style="height: 20rpx;" mode=""></image> 
						</span>
						<text>{{ eye ? '******' :'0.00'}}</text>
					</view>
				</view>
				<span class="CardDali-text" @click="GoCardDatali">
					查看详情
				</span>
			</view>
			<view class="CardDali-btn">
				<view class="btn" v-for="(item,index) in cardBtn" :key="index"  :style="{border:index+1 === cardBtn.length ?  'none':'1px soilid #ddd'}" @click="GetIndex(index)">
					{{item}}
				</view>
			</view>
		</view>
		<view class="Account-Add">
			<view class="btn" :class="{selectBtn:index === 1 ? true : false}" v-for="(item,index) in Add" :key="index">
				{{item}}
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		name:"DebitCard",
		data() {
			return {
					cardBtn:['查明细','去转账','买理财','去存款'],
					Add:['开通电子账户','添加新卡片'],
					eye:true
			};
		},
		methods:{
			GetIndex(index){
				console.log(index);
				index === 0 ? uni.navigateTo({
					url:'/pages/Details/Details'
				}):''
				index === 1 ? uni.navigateTo({
					url:'/pages/remittance/remittance'
				}):''
			},
			NextEye(){
				this.eye = !this.eye
			},
			GoCardDatali(){
				uni.navigateTo({
					url:'/pages/CardDatali/CardDatali'
				})
			}
		}
	}
</script>

<style lang="scss" scoped>
	.Account-CardDali{
		width: 95%;
		margin: 0 auto;
		background-color: #fff;
		margin-top: 20rpx;
		border-radius: 10rpx;
		.CardDali-title{
			padding:30rpx;
			display: flex;
			justify-content: space-between;
			.title-box{
				display: flex;
				align-items: center;
				image{
					width: 30rpx;
					height: 15rpx;
					margin: 0 10rpx;
				}
				text{
					font-size: 28rpx; 
					color: #888;
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
			padding:0 20rpx;
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
						height: 15rpx;
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
			.CardDali-text{
				font-size: 25rpx;
				color: #7c4bb6;
			}
		}
		.CardDali-btn{
			padding: 30rpx;
			margin: 0 auto;
			display: flex;
			justify-content: space-between;
			align-items: center;
			border-top: 1px solid #ddd;
			margin-top: 20rpx;
			.btn{
				display: flex;
				align-items: center;
				height: 30rpx;
				border-right: 1px solid #ddd;
				padding: 0 30rpx;
				color: #7c47be;
				font-size: 28rpx;
			}
		}
	}
	.Account-Add{
		flex: 1;
		padding: 0 30rpx;
		margin: 0 auto;
		display: flex;
		justify-content: space-between;
		.btn{
			border: 1px solid;
			padding: 20rpx 80rpx;
			border-radius: 50rpx;
			color: #6d4b98;
			margin-top: 40rpx;
		}
		.selectBtn{
			background-color: #7d38d1;
			color: #fff;
		}
	}
</style>