<template>
	<view class="wealth-invest" :style="{ background: `url(${url})`,backgroundSize:'100%',backgroundRepeat:'no-repeat',backgroundColor:'#fff'}">
		<view class="invest-title">
			<view class="title">
				{{title}} <image src="@/static/nine_search_right_arrow.png" mode=""></image>
			</view>
			<p>{{SubTitle}}</p>
		</view>
		<view class="wealth-invest-textBox" style="border-bottom: 1px solid #efefef;" v-for="(item,index) in wealthInvest" :key="index">
			<view class="Optimal-money">
				<view class="money-title">
					{{item.name}}
				</view>
				<view class="Optimal-list">
					<view class="Optimal-list-left">
						<p class="Optimal-list-left-MaxTitle">{{item.percentage}}</p>
						<p class="Optimal-list-left-MiniTitle">{{item.percentageSuhTitle}}</p>
					</view>	
					<view class="Optimal-list-rigth">
						<p class="Optimal-list-left-MaxTitle">{{item.datali}}</p>
						<p class="Optimal-list-left-MiniText">
							<text v-for="(sub,num) in item.subDatali" :key="num" :style="{'border-right' : num+1 === item.subDatali.length ? 'none' : '1px solid #ccc'}" >{{sub}}</text>
						</p>
					</view>
				</view>
				<view class="Optimal-tisi">
					<view class="Optimal-tisi-text-icon">
						<view class="tisi-text">
							{{item.prompt}}
						</view>
						<view class="tisi-icon">
							<image src="@/static/nine_search_right_arrow.png" mode=""></image>
						</view>
					</view>
					<p>{{item.SubTitlePrompt}}</p>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		name:"wealth-invest",
		data() {
			return {
				
			};
		},
		props:{
			wealthInvest:{
				type:[Object,Array]
			},
			url:{
				type:String
			},
			title:{
				type:String
			},
			SubTitle:{
				type:String
			}
		}
	}
</script>

<style lang="scss" scoped>
	.wealth-invest{
		width: 90%;
		background: #fff;
		margin: 0 auto;
		border-radius: 20rpx;
		margin-top: 20rpx;
		background-color: #fff;
		.invest-title{
			height: 100rpx;
			padding: 10rpx 20rpx;
			line-height: 45rpx;
			.title{
				margin-top: 20rpx;
				display: flex;
				align-items: center;
				font-size: 35rpx;
				image{
					width: 30rpx;
					height: 30rpx;
				}
			}
			p{
				width: 100%;
				font-size: 25rpx;
				color: #888;
			}
		}
		.wealth-invest-textBox{
			width: 100%;
			margin: 0 auto;
			background-color: #fff;
			.Optimal-money{
				padding: 20rpx;
				margin-top: 20rpx;
				.money-title{
					margin: 0 auto;
					font-size: 28rpx;
					color: #666;
					.uni-tag{
						background-color: #eff6ff; border-color: #eff6ff; color: #2979ff; font-weight:bold;
					}
				}
				.Optimal-list{
					margin: 0 auto;
					padding-bottom: 20rpx;
					display: flex;
					align-items: center;
					justify-content: center;
					.Optimal-list-left{
						width: 45%;
						.Optimal-list-left-MaxTitle{
							font-size: 35rpx;
							color: #c5663b;
							font-weight: bold;
							margin: 10rpx auto;
						}
						.Optimal-list-left-MiniTitle{
							font-size: 23rpx;
							color: #888;
						}
					}
					.Optimal-list-rigth{
						flex: 1;
						.Optimal-list-left-MaxTitle{
							font-size: 30rpx;
							margin: 10rpx auto;
							padding: 0 15rpx;
						}
						.Optimal-list-left-MiniText{
							font-size: 23rpx;
							color: #888;
							text{
								padding: 0 15rpx;
								border-right:1px solid #ccc ;
							}
						}
					}
				}
				.Optimal-tisi{
					width: 100%;
					background-color: #fafafa;
					.Optimal-tisi-text-icon{
						width: 100%;
						display: flex;
						justify-content: space-between;
						margin-top: 10rpx;
						padding: 10rpx;
						.tisi-text{
							width: 90%;
							color: #888;
							font-size: 23rpx;
						}
						.tisi-icon{
							flex: 1;
							transform: rotateZ(90deg);
							display: flex;
							justify-content: center;
							align-self: self-start;
							image{
								width: 25rpx;
								height: 25rpx;
							}
						}
					}
					p{
						font-size: 23rpx;
						color: #888;
						padding:0 10rpx 10rpx 10rpx;
					}
				}
			}
		}
	}
</style>