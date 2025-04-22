<template>
	<view class="higlights-title">
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
	</view>
</template>

<script>
	import occupyVue from './occupy.vue';
	export default {
		name:"higlights-title",
		data() {
			return {
				tabList: ['关注','推荐','讨论','财富','汽车'],
				current: 1, // tabs组件的current值，表示当前活动的tab选项
				TabsBg:'none',
			};
		},
		components:{
			occupyVue
		}
	}
</script>

<style lang="scss" scoped>
	.higlights-title{
		background-color: #fff;
		position: fixed;
		width: 100%;
		z-index: 999;
		top: 0;
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
	}
	
	
</style>