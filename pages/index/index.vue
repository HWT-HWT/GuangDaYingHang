<template>
	<view class="index">
		<view>
			<HomeTitleVue ></HomeTitleVue>
		</view>
		<view style="position: fixed; top: 0; z-index: 999;" :style="{'opacity' : scrollTop>=100 ? '1' : '0'}">
			<HomeTitleVue BgColor="#fff"></HomeTitleVue>
		</view>
		
		<view class="index-box"></view>
		
		<view class="index-viewBox">
			<ListViewVue :listTitle="listTitle" :sizi="'70rpx'" @GetIndex='GoLogin'></ListViewVue>
		</view>
		
		<view class="index-ViewList">
			<ListViewVue :listTitle="listView" :sizi="'65rpx'" :BgColor="'#fff'" :FontSize="'25rpx'" :Pad="'45rpx 0 '" @GetIndex='GetIndex'></ListViewVue>
		</view>
		
		<view class="index-notice">
			<view class="notice-text">
				<image src="@/static/home_scroll_jj.png" mode=""></image>
				<text>聚焦</text>
			</view>
			<p>事关收入!各省份最新最低工资…</p>
			<image src="@/static/upsdk_payment_right.webp" mode=""></image>
		</view>
		
		<view class="index-banner">
			<swiper :indicator-dots="true" :autoplay="true" :interval="3000" :duration="1000">
				<swiper-item v-for="(item,index) in 4" :key="index">
					<image :src="`../../static/home-banner-${index+1}.png`" mode=""></image>
				</swiper-item>
			</swiper>
		</view>
		
		<view class="index-wealth">
			<view class="wealth-title">
				<titleVue :icon="true" :LFontSize="'35'" RColor="#bbb" :RFontSize="'28'" IconSize="0.8">
					<template #left>
						财富精选
					</template>
					<template #rigth>
						更多
					</template>
				</titleVue>
			</view>
			<view class="wealth-box">
				<view class="wealth-swiper">
					<swiper :indicator-dots="true" :autoplay="true" :interval="3000" :duration="1000">
						<swiper-item v-for="(item,index) in 3" :key="index">
							<view class="swiper-item">
								<view class="title">
									<p>新客专属</p>
									<span>特邀开启光大银行理财初体验</span>
								</view>
								<view class="content">
									查看详情
								</view>
								<view class="btn">
									立即购买
								</view>
							</view>
						</swiper-item>
					</swiper>
				</view>
				<view class="wealth-Text">
					<view class="top">
						<p>证券开户</p>
						<view class="datali">
							<p>详情</p>
							<span>点击了解</span>
						</view>
					</view>
					<view class="bottom">
						<titleVue :LFontSize="'25'" RColor="#bbb" :RFontSize="'20'" width="90%" :icon="true" IconSize="0.8">
							<template #left>
								现金理财榜
							</template>
						</titleVue>
					</view>
				</view>
			</view>
		</view>
	
		<view class="index-wealth-list">
			<view class="wealth-list-box" v-for="(item,index) in 3" :key="index">
				<image :src="`../../static/wealth-bj-${index+1}.png`" mode=""></image>
			</view>
		</view>
	
		<view class="index-Pension">
			<titleVue LFontSize="35">
				<template #left>
					养老金融
				</template>
			</titleVue>
			
			<view class="Pension-image"></view>
			
			<view class="Pension-Row">
				<view class="Row" v-for="(item,index) in 2" :key="index">
					<image :src="`../../static/Pension-bj-${index+1}.png`" mode=""></image>
				</view>
			</view>
		</view>

		<view class="index-highlights">
			<titleVue :icon="true" IconSize="0.8" RColor="#a0a0a0" RFontSize="25">
				<template #left>
					今日看点
				</template>
				<template #rigth>
					更多
				</template>			
			</titleVue>
			
			<view class="highlights-box">
				<view class="highlights-title">
					<image src="@/static/highlights-bj-1.png" mode=""></image>
				</view>
				<scrollBtnVue :list="wealthInvest"></scrollBtnVue>
				<view class="highlights-listView">
					<image src="../../static/highlights-bj-2.png" mode=""></image>
					<view class="highlights-Text">
						<p>从红包到财富:压岁钱…</p>
						<span>看详情 </span>
					</view>
				</view>
				<view class="highlights-listView" style="border: none;">
					<image src="../../static/highlights-bj-2.png" mode=""></image>
					<view class="highlights-Text">
						<p>从红包到财富:压岁钱…</p>
						<span>看详情 </span>
					</view>
				</view>
			</view>
		
		</view>
	
		<view class="index-highlights-Swiper">
			<view class="highlights-Swiper">
				<swiper :indicator-dots="true" :autoplay="true" :interval="3000" :duration="1000">
					<swiper-item>
						<image src="@/static/highlights-Swiper-1.png" mode=""></image>
					</swiper-item>
				</swiper>
			</view>
			<view class="highlights-Text">
				<image src="@/static/highlights-Swiper-2.png" mode=""></image>
			</view>
		</view>
	
		<view class="index-service">
			<titleVue LFontSize="30" :icon="true" RColor="#afafaf" IconSize="0.9">
				<template #left>
					权益服务
				</template>
				<template #rigth>
					更多
				</template>
			</titleVue>
			
			<view class="service-centent">
				<view class="left">
					<view class="left-text">
						<p>超值绑</p>
						<p class="span">首绑得立减金</p>
						<text>去查看</text>
					</view>
				</view>
				<view class="right">
					<view class="Row" v-for="(item,index) in 2" :key="index">
						<image :src="`../../static/service-icon-${index+1}.png`" mode=""></image>
					</view>
				</view>
			</view>
		</view>
	
		<view class="index-shopping">
			<titleVue LFontSize="30" :icon="true" RColor="#afafaf" IconSize="0.9">
				<template #left>
					精彩商城
				</template>
				<template #rigth>
					更多
				</template>
			</titleVue>
			<view class="shopping-image">
				<image src="@/static/shopping-1.png" mode=""></image>
			</view>
		</view>
		
		<view class="index-characteristic">
			<titleVue LFontSize="30"  RColor="#afafaf">
				<template #left>
					特色服务
				</template>
			</titleVue>
			
			<view class="characteristic-centent">
				<view class="left">
					<view class="left-text">
						<p>理财夜市</p>
						<p class="span">好选择 财安心</p>
						<text>理财产品 </text>
					</view>
				</view>
				<view class="right">
					<view class="Row" v-for="(item,index) in 2" :key="index">
						<image :src="`../../static/service-icon-1-${index+1}.png`" mode=""></image>
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	import occupyVue from '../../components/occupy.vue'
	import ListViewVue from '../../components/ListView.vue'
	import titleVue from '../../components/titleVue.vue'
	import HomeTitleVue from '../../components/HomeTitle.vue'
	import scrollBtnVue from '../../components/scroll-btn.vue'
	export default {
		data() {
			return {
				listTitle:[
					{
						name:'账户',
						icon:'../../static/Home-icon-1.png'
					},
					{
						name:'明细',
						icon:'../../static/Home-icon-2.png'
					},
					{
						name:'转账',
						icon:'../../static/Home-icon-3.png'
					},
					{
						name:'支付',
						icon:'../../static/Home-icon-4.png'
					},
				],
				listView:[
					{
						name:'存款',
						icon:'../../static/Home-listIcon-1.png'
					},
					{
						name:'缴费',
						icon:'../../static/Home-listIcon-2.png'
					},
					{
						name:'资产',
						icon:'../../static/Home-listIcon-3.png'
					},
					{
						name:'信用卡',
						icon:'../../static/Home-listIcon-4.png'
					},
					{
						name:'贷款',
						icon:'../../static/Home-listIcon-5.png'
					},
					{
						name:'贷款',
						icon:'../../static/Home-listIcon-6.png'
					},
					{
						name:'基金',
						icon:'../../static/Home-listIcon-7.png'
					},
					{
						name:'个人养老金',
						icon:'../../static/Home-listIcon-8.png'
					},
					{
						name:'权益服务',
						icon:'../../static/Home-listIcon-9.png'
					},
					{
						name:'全部',
						icon:'../../static/Home-listIcon-10.png'
					}
				],
				scrollTop:0,
				wealthInvest:['PK投票','热门讨论','热点问答','精选推荐'],
			}
		},
		methods: {
			GoLogin(index){
				console.log(index);
				
				if(uni.getStorageSync('account')){
					index === 0 ? uni.navigateTo({
						url:'/pages/Account/Account'
					}) : ''
					index === 1 ? uni.navigateTo({
						url:'/pages/Details/Details'
					}) : ''
					index === 2 ? uni.navigateTo({
						url:'/pages/transfer/transfer'
					}) : ''
				}else{
					uni.navigateTo({
						url:'/pages/gesture/gesture'
					})
				}
			},
			GetIndex(index){
				console.log(index);
				if(uni.getStorageSync('account')){
					index === 2 ? uni.navigateTo({
						url:'/pages/property/property'
					}) : ''
					index === 4 ? uni.navigateTo({
						url:'/pages/loan/loan'
					}) : ''
				}else{
					uni.navigateTo({
						url:'/pages/gesture/gesture'
					})
				}
			}
		},
		components:{
			occupyVue,
			ListViewVue,
			titleVue,
			HomeTitleVue,
			scrollBtnVue
		},
		onPageScroll(Scroll) {
			this.scrollTop =  Scroll.scrollTop
		}
	}
</script>

<style scoped lang="scss">
	.index{
		width: 100vw;
		background:url('@/static/index-bg-1.png') no-repeat;
		background-size: 100% ;
		background-color: #f8f8f8;
		padding-bottom: 50rpx;
		.index-title{
			width: 100%;
			display: flex;
			align-items: center;
			.title-image{
				width: 90rpx;
				height: 90rpx;
				padding-left: 30rpx;
			}
			.position{
				display: flex;
				align-items: center;
				font-size: 30rpx;
				image{
					width: 25rpx;
					height: 25rpx;
				}
			}
			.input-Box{
				flex: 1;
				display: flex;
				align-items: center;
				border: 1px solid #ccc;
				padding: 10rpx;
				margin: 0 20rpx;
				border-radius: 50rpx;
				input{
					flex: 1;
					padding: 5rpx 10rpx;
					font-size: 24rpx;
				}
				image{
					width: 30rpx;
					height: 30rpx;
					margin: 0 10rpx;
				}
			}
			.icon{
				image{
					width: 40rpx;
					height: 40rpx;
					padding-right: 30rpx;
					padding-left: 20rpx;
				}
			}
		}
		.index-box{
			width: 100%;
			height: 260rpx;
			display: flex;
			align-items: center;
			justify-content: center;
		}
		.index-listTitle{
			display: flex;
			width: 90%;
			margin: 0 auto;
			justify-content: space-between;
		}
		.index-ViewList{
			width:100%;
			margin: 0 auto;
			margin-top: 20rpx;
		}
		.index-notice{
			width: 90%;
			margin: 0 auto;
			display: flex;
			justify-content: space-evenly;
			align-items: center;
			padding: 35rpx 0;
			background-color: #fff;
			margin-top: 30rpx;
			border-radius: 10rpx;
			.notice-text{
				display: flex;
				align-items: center;
				image{
					width: 40rpx;
					height: 40rpx;
				}
				font-size: 30rpx;
			}
			p{
				font-size: 28rpx;
				width: 60%;
				color: #555;
			}
			image{
				width: 40rpx;
				height: 40rpx;
			}
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
		.index-wealth{
			width: 90%;
			margin: 0 auto;
			.wealth-box{
				width: 100%;
				height: 500rpx;
				display: flex;
				justify-content: space-between;
				.wealth-swiper{
					width: 49%;
					border-radius: 20rpx;
					swiper{
						width: 100%;
						height: 100%;
						/deep/.uni-swiper-dot{
							width: 10rpx;
							height: 5rpx;
							border-radius: 10rpx;
						}
						/deep/.uni-swiper-dot-active{
							width: 20rpx;
							height: 5rpx;
							border-radius: 10rpx;
							background-color: blue;
						}
						swiper-item{
							width: 100%;
							height: 100%;
							background: url('../../static/wealth-banner-bj.png');
							background-size: 100% 100%;
							.swiper-item{
								width: 90%;
								height: 100%;
								display: flex;
								align-items: center;
								margin: 0 auto;
								flex-wrap: wrap;
								.title{
									p{
										font-size: 30rpx;
									}
									span{
										font-size: 22rpx;
										color: #636363;
									}
								}
								.content{
									width: 100%;
									font-size: 25rpx;
									color: #636363;
								}
								.btn{
									background-color: #d95a2a;
									padding: 10rpx;
									color: #fff;
									border-radius: 50rpx;
									font-size: 25rpx;
									padding:10rpx 30rpx;
									
								}
							}
						}
					}
				}
				.wealth-Text{
					width: 49%;
					border-radius: 20rpx;
					display: flex;
					flex-wrap: wrap;
					align-items: center;
					justify-content: space-between;
					.top{
						width: 100%;
						display: flex;
						justify-content: space-between;
						align-items: center;
						border-radius: 20rpx;
						background-color: #f8f4eb;
						padding: 20rpx;
						p{
							font-size: 30rpx;
							color: #9b7761;
							font-weight: bold;
						}
						.datali{
							display: flex;
							flex-wrap: wrap;
							align-items: center;
							justify-content: center;
							
							p{
								width: 100%;
								font-size: 30rpx;
								color: #d75933;
								text-align: center;
								font-weight: normal;
							}
							span{
								font-size: 22rpx;
								margin-top: 5rpx;
								color: #6b675e;
							}
						}
					}
					.bottom{
						background: url('../../static/wealth-bj.png');
						background-size: 100% 100%;
						width: 100%;
						height: 74%;
						border-radius: 20rpx;
					}
				}
			}
		}
		.index-wealth-list{
			width: 90%;
			margin: 0 auto;
			margin-top: 20rpx;
			display: flex;
			align-items: center;
			justify-content: space-between;
			.wealth-list-box{
				width: 32%;
				height: 100%;
				border-radius: 20rpx;
				image{
					width: 100%;
					height: 140rpx;
				}
			}
		}
		.index-Pension{
			width: 90%;
			margin: 0 auto;
			.Pension-image{
				width: 100%;
				height: 180rpx;
				border-radius: 20rpx;
				background: url('@/static/Pension-bj.png');
				background-size: 100% 100%;
			}
			.Pension-Row{
				width: 100%;
				margin-top: 10rpx;
				display: flex;
				justify-content: space-between;
				align-items: center;
				.Row{
					width: 49%;
					height: 100%;
					border-radius: 20rpx;
					image{
						width: 100%;
						height: 190rpx;
					}
				}
			}
		}
		.index-highlights{
			width: 90%;
			margin: 0 auto;
			margin-top:30rpx;
			.highlights-box{
				background: linear-gradient(to bottom, #ffffff 50%, #edf3ff);
				padding: 20rpx;
				border-radius: 20rpx;
				.highlights-title{
					width: 100%;
					height: 30rpx;
					image{
						width: 200rpx;
						height: 100%;
					}
				}
				.highlights-listView{
					width: 100%;
					display: flex;
					padding-bottom: 20rpx;
					margin-top: 20rpx;
					border-bottom: 1px solid #ddd;
					image{
						width: 180rpx;
						height: 100rpx;
					}
					.highlights-Text{
						margin-left: 20rpx;
						display: flex;
						flex-wrap: wrap;
						align-items: center;
						p{
							width: 100%;
							font-size: 28rpx;
						}
						span{
							font-size: 23rpx;
							color: #cb805d;
						}
					}
				}
			}
		}
		.index-highlights-Swiper{
			width: 90%;
			height: 400rpx;
			margin: 0 auto;
			margin-top: 20rpx;
			display: flex;
			justify-content: space-between;
			.highlights-Swiper{
				width: 49%;
				border-radius: 20rpx;
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
						background-color: #753cba;
					}
					swiper-item{
						border-radius: 20rpx;
						image{
							width: 100%;
							height: 100%;
						}
					}
				}
			}
			.highlights-Text{
				width: 49%;
				border-radius: 20rpx;
				image{
					width: 100%;
					height: 100%;
					border-radius: 20rpx;
				}
			}
		}
		.index-service{
			width: 90%;
			margin: 0 auto;
			.service-centent{
				width: 100%;
				height: 400rpx;
				display: flex;
				justify-content: space-between;
				.left{
					width: 49%;
					height: 100%;
					border-radius: 20rpx;
					background: url('@/static/service-bj-1.png');
					background-size: 100% 100%;
					.left-text{
						height: 200rpx;
						padding: 30rpx;
						display: flex;
						flex-wrap: wrap;
						p{
							width: 100%;
							font-size: 30rpx;
						}
						.span{
							font-size: 25rpx;
							margin-top: -30rpx;
							color: #555;
						}
						text{
							font-size: 25rpx;
							color: #c56544;
						}
					}
				}
				.right{
					width: 49%;
					height: 100%;
					display: flex;
					flex-wrap: wrap;
					align-items: center;
					border-radius: 20rpx;
					.Row{
						width: 100%;
						height: 47%;
						border-radius: 20rpx;
						image{
							width: 100%;
							height: 100%;
							border-radius: 20rpx;
						}
					}
				}
			}
		}
		.index-shopping{
			width: 90%;
			margin: 0 auto;
			.shopping-image{
				width: 100%;
				image{
					width: 100%;
					height: 200rpx;
				}
			}
		}
		.index-characteristic{
			width: 90%;
			margin: 0 auto;
			.characteristic-centent{
				width: 100%;
				height: 400rpx;
				display: flex;
				justify-content: space-between;
				.left{
					width: 49%;
					height: 100%;
					border-radius: 20rpx;
					background: url('@/static/service-bj-2.png');
					background-size: 100% 100%;
					.left-text{
						height: 200rpx;
						padding: 30rpx;
						display: flex;
						flex-wrap: wrap;
						p{
							width: 100%;
							font-size: 30rpx;
						}
						.span{
							font-size: 25rpx;
							margin-top: -30rpx;
							color: #555;
						}
						text{
							font-size: 25rpx;
							color: #c56544;
						}
					}
				}
				.right{
					width: 49%;
					height: 100%;
					display: flex;
					flex-wrap: wrap;
					align-items: center;
					border-radius: 20rpx;
					.Row{
						width: 100%;
						height: 47%;
						border-radius: 20rpx;
						image{
							width: 100%;
							height: 100%;
							border-radius: 20rpx;
						}
					}
				}
			}
		}
	}
</style>
