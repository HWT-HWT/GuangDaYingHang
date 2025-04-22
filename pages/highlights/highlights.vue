<template>
	<view  class="highlights">
		<view class="highlights-top-title">
			<occupyVue hight="80rpx"></occupyVue>
			<view class="highlights-title">
				<view class="LeftText">
					<image src="@/static/highlights-title-icon.png" mode=""></image>
					<text>年化收益最高超3%!低利率时代...</text>
				</view>
				<image class="rightIcon" src="@/static/icon_main_page_search.png" mode=""></image>
			</view>
		</view>
		<view class="highlights-Tabs">
			 <z-tabs ref="tabs" :list="tabList" :current="current" :bg-color='TabsBg' active-color='#7a41c6' />
		</view>
		
		<higlightsTitleVue v-if="scrollTop>100? true:false"></higlightsTitleVue>
		
		<view class="index-highlights">
			<view class="highlights-box">
				
				<view class="highlights-title">
					<image src="@/static/highlights-bj-1.png" mode=""></image>
					<view class="RightText">
						进入社区 <image src="@/static/right_arr2.webp" mode=""></image>
					</view>
				</view>
				
				<view class="highlights-listView">
					<view class="title"> <image src="@/static/sunshine_question_icon.png" mode=""></image> 2025年大降息?怎么做能让资产不…</view>
					<view class="subtitle"> <image src="@/static/sunshine_answer_icon.png" mode=""></image> 从目前的市场动态和经济形势来看，降息的可能…</view>
					<view class="subtitle"> <image src="@/static/sunshine_answer_icon.png" mode=""></image> 据一些专家和机构的分析，2025年降息的可能性…</view>
				</view>
				
				<view class="highlights-notice">
					<view class="notice-Icon">
						<image src="../../static/speaker-icon-1.png" mode=""></image>
						进入金知了社区，结交志同道合的投资好友!
					</view>
					<image src="@/static/right_arr2.webp" mode=""></image>
				</view>
			</view>
		</view>
		<view class="highlights-Swiper">
			<swiper :indicator-dots="true" :autoplay="true" :interval="3000" :duration="1000">
				<swiper-item v-for="(item,index) in 3" :key="index">
					<view class="Swiper">
						<p>快速崛起的国产A点燃科技行情，怎…</p>
						<view class="text">了解详情</view>
					</view>
					<view class="Swiper-image">
						<image src="@/static/highlights-Swiper-3.png" mode=""></image>
					</view>
				</swiper-item>
			</swiper>
			<view class="Text">
				<view class="Text-View">
					<view class="span">
						<image src="@/static/icon-1.png" mode=""></image>
						这个春节你花了多少钱?
					</view>
					<view class="text">
						压岁钱收了6000、...
					</view>
				</view>
				<view class="Text-View" style="margin-top: 15rpx;">
					<view class="span">
						<image src="@/static/icon-1.png" mode=""></image>
						 理财课程
					</view>
					<view class="text">
						上班族实用理财提升课
					</view>
				</view>
			</view>
		</view>
		<view class="highlights-image">
			<view class="title">
				<image src="@/static/highlights-bj-4.png" mode=""></image>
				<view class="Text">
					更多 <image src="@/static/nine_search_right_arrow.png" mode=""></image>
				</view>
			</view>
			
			<view class="listView">
				<view class="list" v-for="(item,index) in listView" :key="index">
					<image :src="`../../static/icon-${index+2}.png`" mode=""></image>
					{{item}}
				</view>
			</view>
			
			<view class="subscribe">
				<view class="subscribe-icon-text">
					<image src="../../static/icon-qiezi-1.png" mode=""></image>
					热点专业解读，洞见投资方向
				</view>
				<image src="@/static/nine_search_right_arrow.png" mode=""></image>
			</view>
		</view>
		<view class="highlights-Zooz">
			<titleVue LFontSize="32" :icon="true" RColor="#aaaaaa">
				<template #left>
					精选专题
				</template>
				<template #rigth>
					全部
				</template>
			</titleVue>
			<scroll-view class="scroll-view_H" scroll-x="true" scroll-left="120">
				<view class="scroll-view-item_H">
					<image src="@/static/highlights-Zooz-1.png" mode=""></image>
					<image src="@/static/highlights-Zooz-2.png" mode=""></image>
				</view>
			</scroll-view>
		</view>
	</view>
</template>

<script>
	import occupyVue from '../../components/occupy.vue'
	import titleVue from '../../components/titleVue.vue'
	import higlightsTitleVue from '../../components/higlights-title.vue'
	export default {
		data() {
			return {
				tabList: ['关注','推荐','讨论','财富','汽车'],
				current: 1, // tabs组件的current值，表示当前活动的tab选项
				TabsBg:'none',
				listView:['年化收益最高超3%!低利率时代，这类低风险…','黄金又暴涨!为什么近些年黄金会一直涨?','爆了!DeepSeek席卷资本市场，这3个方向值…'],
				scrollTop: 0,
			}
		},
		methods: {
			
		},
		components:{
			occupyVue,
			titleVue,
			higlightsTitleVue
		},
		onPageScroll(Scroll) {
			this.scrollTop = Scroll.scrollTop
		}
	}
</script>

<style scoped lang="scss" scoped> 
	.highlights{
		width: 100vw;
		padding-bottom: 50rpx;
		background-color: #f7f7f7;
		.highlights-top-title{
			background-color: #fff;
			.highlights-title{
				width: 90%;
				margin: 0 auto;
				display: flex;
				align-items: center;
				justify-content: space-between;
				padding: 20rpx;
				.LeftText{
					display: flex;
					align-items: center;
					image{
						width: 65rpx;
						height: 65rpx;
					}
					text{
						margin-left: 30rpx;
						font-size: 30rpx
					}
				}
				
				.rightIcon{
					width: 45rpx;
					height: 45rpx;
				}
			}
		}
		.highlights-Tabs{
			width: 100%;
		}
		.index-highlights{
			width: 90%;
			margin: 0 auto;
			margin-top:30rpx;
			.highlights-box{
				background: linear-gradient(to bottom, #ffffff 50%, #edf3ff);
				padding: 30rpx 20rpx;
				border-radius: 20rpx;
				.highlights-title{
					width: 95%;
					margin: 0 auto;
					margin-top: 10rpx;
					height: 30rpx;
					display: flex;
					align-items: center;
					justify-content: space-between;
					image{
						width: 200rpx;
						height: 100%;
					}
					.RightText{
						font-size: 24rpx;
						padding:10rpx 20rpx;
						border-radius: 50rpx;
						background-color: #f6f6f6;
						border:1px solid #f1f1f1;
						image{
							margin-left: 10rpx;
							width: 10rpx;
							height: 15rpx;
						}
					}
				}
				.highlights-listView{
					width: 100%;
					padding-bottom: 10rpx;
					margin-top: 30rpx;
					line-height: 65rpx;
					image{
						width: 40rpx;
						height: 40rpx;
						margin:10rpx;
						border-radius: 20rpx;
					}
					.title{
						font-size: 34rpx;
						display: flex;
						align-items: center;
					}
					.subtitle{
						font-size: 24rpx;
						display: flex;
						align-items: center;
					}
				}
				.highlights-notice{
					margin: 0 auto;
					margin-top: 10rpx;
					display: flex;
					align-items: center;
					justify-content: space-between;
					background-color: #fff;
					border-radius: 50rpx;
					padding:15rpx 20rpx;
					.notice-Icon{
						display: flex;
						align-items: center;
						font-size: 23rpx;
						image{
							margin-right: 10rpx;
							width: 50rpx;
							height: 50rpx;
						}
					}
					image{
						width: 12rpx;
						height: 18rpx;
					}
				}
			}
		}
		.highlights-Swiper{
			width: 90%;
			height: 400rpx;
			margin: 0 auto;
			margin-top: 20rpx;
			display: flex;
			justify-content: space-between;
			align-items: center;
			view{
				border-radius: 20rpx;
			}
			swiper{
				width: 49%;
				height: 100%;
				background-color: #fff;
				border-radius: 20rpx;
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
				.Swiper{
					padding: 20rpx;
					p{
						font-size: 30rpx;
					}
					.text{
						margin-top:15rpx;
						font-size: 24rpx;
						color: #ba7250;
					}
				}
				.Swiper-image{
					width: 90%;
					margin: 0 auto;
					image{
						width: 300rpx;
						height: 200rpx;
					}
				}
			}
			.Text{
				width: 49%;
				height: 100%;
				.Text-View{
					width: 100%;
					height: 48%;
					background-color: #fff;
					.span{
						width: 90%;
						margin: 0 auto;
						padding-top: 20rpx;
						display: flex;
						padding-bottom: 20rpx;
						font-size: 28rpx;
						image{
							width: 50rpx;
							height: 50rpx;
						}
					}
					.text{
						width: 85%;
						margin: 0 auto;
						padding: 5rpx;
						font-size: 22rpx;
					}
				}
			}
		}
		.highlights-image{
			width: 90%;
			padding-bottom: 20rpx;
			margin: 0 auto;
			margin-top: 20rpx;
			border-radius: 20rpx;
			background: linear-gradient(to bottom, #fff 70%,#fcf0e4);
			.title{
				width: 90%;
				margin: 0 auto;
				padding-top: 20rpx;
				justify-content: space-between;
				align-items: center;
				display: flex;
				image{
					width: 200rpx;
					height: 70rpx;
				}
				.Text{
					font-size: 25rpx;
					background-color: #f8f8f8;
					padding:8rpx 20rpx;
					text-align: center;
					border-radius: 50rpx;
					border: 1px solid #bbb;
					display: flex;
					align-items: center;
					justify-content: center;
					image{
						margin-left: 5rpx;
						width: 25rpx;
						height: 25rpx;
					}
				}
			}
			.listView{
				width: 90%;
				margin: 0 auto;
				line-height: 60rpx;
				margin-top: 20rpx;
				.list{
					display: flex;
					align-items: center;
					font-size: 25rpx;
					image{
						width: 50rpx;
						height: 50rpx;
					}
				}
			}
			.subscribe{
				width: 90%;
				background-color: #fff;
				margin: 0 auto;
				margin-top: 20rpx;
				font-size: 23rpx;
				display: flex;
				align-items: center;
				justify-content: space-between;
				padding: 10rpx 20rpx;
				border-radius: 50rpx;
				.subscribe-icon-text{
					display: flex;
					align-items: center;
					image{
						margin-top: 10rpx;
						width: 170rpx;
						height: 60rpx;
					}
				}
				image{
					width: 25rpx;
					height: 25rpx;
				}
			}
		}
		.highlights-Zooz{
			width: 80%;
			margin: 0 auto;
			background-color: #fff;
			padding:0 25rpx;
			margin-top: 20rpx;
			border-radius: 20rpx;
			padding-bottom: 30rpx;
			.scroll-view-item_H {
				width: 1000rpx;
				display: flex;
				height: 300rpx;
				line-height: 300rpx;
				text-align: center;
				font-size: 36rpx;
				image{
					width:500rpx;
					height: 100%;
					margin-left: 20rpx;
				}
			}
		}
	}
</style>
