<template>
	<view class="activity">
		<occupyVue hight="90rpx"></occupyVue>
		<view class="activity-title">
			<view class="position">
				<text>北京</text>
				<image src="@/static/icon_main_page_arrow_down.png" mode=""></image>
			</view>
			
			<view class="switch">
				<view class="Row Selected" >
					活动
				</view>
				<view class="Row">
					会员
				</view>
			</view>
			
			<view class="qiezi">
				<image src="@/static/btn_main_page_help.gif" mode=""></image>
			</view>
			
			<view class="icon">
				<image src="@/static/btn_main_page_msg.png" mode=""></image>
			</view>
		</view>
		<view class="activity-title-banner">
			<swiper :indicator-dots="true" :autoplay="true" :interval="3000" :duration="1000">
				<swiper-item v-for="(item,index) in 5" :key="index">
					<image :src="`../../static/activity-banner-${index+1}.png`" mode=""></image>
				</swiper-item>
			</swiper>
		</view>
		<view class="activity-reality">
			<view class="reality-title">
				<titleVue :icon="true">
					<template #left>
						周三现时领取
						<span class="Time">
							10:00
						</span>
					</template>
					<template #rigth>
						更多
					</template>
				</titleVue>
			</view>
			<view class="reality-Image-bg">
				<image src="@/static/activity-bg-1-1.png" mode=""></image>
			</view>
			<view class="reality-Image-bg">
				<image src="@/static/activity-bg-1-2.png" mode=""></image>
			</view>
		</view>
		<view class="activity-Hot">
			<view class="Hot-Title">
				<titleVue :icon="true" RColor="#9d9d9d">
					<template #left>
						热门福利
					</template>
					<template #rigth>
						更多
					</template>
				</titleVue>
			</view>
			<scroll-view class="scroll-view_H" scroll-x="true" scroll-left="120">
				<view class="scroll-view-item_H">
					<image src="@/static/activity--hot-bg-1.png" mode=""></image>
					<image src="@/static/activity--hot-bg-2.png" mode=""></image>
					<image src="@/static/activity--hot-bg-1.png" mode=""></image>
					<image src="@/static/activity--hot-bg-2.png" mode=""></image>
				</view>
			</scroll-view>
		</view>
		<view class="activity-advertisement">
			<swiper :indicator-dots="true" :autoplay="true" :interval="3000" :duration="1000">
				<swiper-item v-for="(item,index) in 4" :key="index">
					<image :src="`../../static/activity-advertisementbg-${index+1}.png`" mode=""></image>
				</swiper-item>
			</swiper>
		</view>
		<view class="activity-Travel">
			<view class="Travel-title">
				<titleVue :LFontW="false">
					<template #left>
						畅享出行
					</template>
				</titleVue>
			</view>
			<view class="index-ViewList">
				<ListViewVue :listTitle="listView" :sizi="'65rpx'" :FontSize="'25rpx'" width="25%"></ListViewVue>
			</view>
		</view>
		<view class="activity-shopping">
			<view class="shopping-title">
				<titleVue :LFontW="false" :icon="true" RColor="#bfbfbf">
					<template #left>
						精彩商城
					</template>
					<template #rigth>
						更多
					</template>
				</titleVue>
				<view class="shopping-image">
					<image src="@/static/activity-shopping-1.png" mode=""></image>
				</view>
			</view>
			<view class="shopping-ListImage">
				<image src="@/static/activity-shopping-image-1.png" mode=""></image>
				<image src="@/static/activity-shopping-image-2.png" mode=""></image>
				<image src="@/static/activity-shopping-image-3.png" mode=""></image>
			</view>
		</view>
		<view class="activity-characteristic">
			<view class="Travel-title">
				<titleVue :LFontW="false">
					<template #left>
						特色服务
					</template>
				</titleVue>
			</view>
			<view class="index-ViewList">
				<ListViewVue :listTitle="characteristic" :sizi="'65rpx'" :FontSize="'25rpx'" width="25%"></ListViewVue>
			</view>
		</view>
		<view class="activity-live">
			<view class="live-title">
				<titleVue :LFontW="false">
					<template #left>
						生活百科大全
					</template>
				</titleVue>
			</view>
			<view class="Zone-ListView">
				<view style="flex: 1;">
					<view class="ListView-Text">
						国家医保局推出“医保影像云索引”，减少患者重复检查
					</view>
					<view class="ListView-SubTitle">
						<text>北京日报客户端</text>
						<text>02-11</text>
					</view>
				</view>
			</view>
			<view class="Zone-ListView">
				<view style="flex: 1;">
					<view class="ListView-Text">
						作为国内领先云计算服务商，联通云与DeepSeek实现多场景…
					</view>
					<view class="ListView-SubTitle">
						<text>中国联通</text>
						<text>02-11</text>
					</view>
				</view>
				<image src="@/static/highlights-bj-3.png" mode=""></image>
			</view>
		</view>
	</view>
</template>

<script>
	import ListViewVue from '../../components/ListView.vue';
	import titleVue from '../../components/titleVue.vue';
	import occupyVue from '../../components/occupy.vue';
	export default {
		data() {
			return {
				listView:[
					{
						name:'标准洗车',
						icon:'../../static/Home-listIcon-1.png'
					},
					{
						name:'车辆保养',
						icon:'../../static/Home-listIcon-2.png'
					},
					{
						name:'空调清洗',
						icon:'../../static/Home-listIcon-3.png'
					},
					{
						name:'车主生活',
						icon:'../../static/Home-listIcon-4.png'
					},
					{
						name:'一线购车',
						icon:'../../static/Home-listIcon-5.png'
					},
					{
						name:'火车票',
						icon:'../../static/Home-listIcon-6.png'
					},
					{
						name:'中青旅遨游',
						icon:'../../static/Home-listIcon-7.png'
					},
					{
						name:'航班管家',
						icon:'../../static/Home-listIcon-8.png'
					},
				],
				characteristic:[
					{
						name:'电影票',
						icon:'../../static/Home-listIcon-3.png'
					},
					{
						name:'海旅免税',
						icon:'../../static/Home-listIcon-4.png'
					},
					{
						name:'惠享健康',
						icon:'../../static/Home-listIcon-5.png'
					},
					{
						name:'缴费',
						icon:'../../static/Home-listIcon-6.png'
					},
					{
						name:'城市服务',
						icon:'../../static/Home-listIcon-7.png'
					},
					{
						name:'联欢惠',
						icon:'../../static/Home-listIcon-8.png'
					},
					{
						name:'权益精选',
						icon:'../../static/Home-listIcon-9.png'
					},
					{
						name:'更多',
						icon:'../../static/Home-listIcon-10.png'
					},
				],
			};
		}, 
		components:{
			titleVue,
			occupyVue,
			ListViewVue
		}
	} 
</script>

<style lang="scss" scoped>
	.activity{
		width: 100vw;
		padding-bottom: 50rpx;
		background-color: #f7f7f7;
		.activity-title{
			display: flex;
			align-items: center;
			justify-content: space-evenly;
			.position{
				display: flex;
				align-items: center;
				font-size: 30rpx;
				image{
					width: 25rpx;
					height: 25rpx;
				}
			}
			.switch{
				width: 340rpx;
				height: 75rpx;
				background:url('@/static/activity-title-1.png') ;
				background-size: 100% 100%;
				margin-left: 20rpx;
				display: flex;
				.Row{
					display: flex;
					align-items: center;
					justify-content: center;
					width: 50%;
					height: 100%;
					text-align: center;
					font-size: 30rpx;
					font-weight: bold;
					color: #888;
				}
				.Selected{
					margin-left: 30rpx;
					font-size: 35rpx;
					color: #000;
				}
			}
			.qiezi{
				image{
					width: 90rpx;
					height: 90rpx;
				}
			}
			.icon{
				image{
					width: 40rpx;
					height: 40rpx;
				}
			}
		}
		.activity-title-banner{
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
		.activity-reality{
			width: 90%;
			margin: 0 auto;
			padding-bottom: 50rpx;
			margin-top: 20rpx;
			background: url('@/static/activity-bg-1.png');
			background-size: 100% 100%;
			border-radius: 20rpx;
			.reality-title{
				width: 90%;
				margin: 0 auto;
				padding-top: 10rpx;
				.Time{
					color: #fff;
					background-color:#fa6d3e ;
					padding:5rpx 10rpx;
					margin-left: 20rpx;
					font-size: 20rpx;
					border-radius: 0 20rpx 0 20rpx;
				}
			}
			.reality-Image-bg{
				width: 85%;
				height: 165rpx;
				margin: 0 auto;
				margin-top: 20rpx;
				image{
					width: 100%;
					height: 100%;
					
				}
			}
		}
		.activity-Hot{
			width: 90%;
			margin: 0 auto;
			background-color: #fff;
			border-radius: 20rpx;
			margin-top: 20rpx;
			padding-bottom: 30rpx;
			.Hot-Title{
				width: 90%;
				margin: 0 auto;
				padding-top: 10rpx;
			}
			.scroll-view-item_H {
				width: 1200rpx;
				display: flex;
				line-height: 300rpx;
				text-align: center;
				font-size: 36rpx;
				image{
					width: 270rpx;
					height: 245rpx;
					margin-left: 20rpx;
				}
			}
		}
		.activity-advertisement{
			width:90%;
			height: 380rpx;
			margin: 0 auto;
			margin-top: 20rpx;
			border-radius: 20rpx;
			swiper{
				width: 100%;
				height: 100%;
				border-radius: 20rpx;
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
				image{
					width: 100%;
					height: 100%;
				}
			}
		}
		.activity-Travel{
			width: 90%;
			margin: 0 auto;
			margin-top: 20rpx;
			border-radius: 20rpx;
			background:url('@/static/activity-Travel-bg-1.png') ;
			background-size: 100% 100%;
			.Travel-title{
				width: 90%;
				margin: 0 auto;
				padding-top: 10rpx;
			}
			.index-ViewList{
				width:100%;
				margin: 0 auto;
				margin-top: 20rpx;
				padding-bottom: 20rpx;
			}
		}
		.activity-shopping{
			width: 90%;
			margin: 0 auto;
			background-color: #fff;
			margin-top: 20rpx;
			border-radius: 20rpx;
			padding-bottom: 20rpx;
			.shopping-title{
				width: 90%;
				margin: 0 auto;
			}
			.shopping-image{
				image{
					width: 100%;
					height: 180rpx;
				}
			}
			.shopping-ListImage{
				width: 90%;
				margin: 0 auto;
				margin-top: 10rpx;
				image{
					width: 200rpx;
					height: 280rpx;
					margin-left: 3rpx;
				}
			}
		}
		.activity-characteristic{
			width: 90%;
			margin: 0 auto;
			margin-top: 20rpx;
			border-radius: 20rpx;
			background-color: #fff;
			.Travel-title{
				width: 90%;
				margin: 0 auto;
				padding-top: 10rpx;
			}
			.index-ViewList{
				width:100%;
				margin: 0 auto;
				margin-top: 20rpx;
				padding-bottom: 20rpx;
			}
		}
		.activity-live{
			width: 90%;
			margin: 0 auto;
			.live-title{
				width: 90%;
				margin: 0 auto;
				padding-top: 10rpx;
			}
			.Zone-ListView{
				padding: 30rpx;
				background-color: #fff;
				border-radius: 20rpx;
				display: flex;
				margin-top: 20rpx;
				.ListView-Text{
					width: 100%;
					height: 100rpx;
					font-size: 25rpx;
				}
				.ListView-SubTitle{
					width: 100%;
					font-size: 20rpx;
					display: flex;
					align-content: center;
					justify-content: space-between;
				}
				image{
					width: 200rpx;
					height: 140rpx;
					margin-left: 50rpx;
				}
			}
		}
	}
</style>
