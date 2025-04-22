<template>
	<view class="HomeTitle" :style="{'background':BgColor}">
		<occupyVue :hight="'80rpx'"></occupyVue>
		<view class="index-title">
			<image class="title-image" src="@/static/btn_main_page_help.gif" mode=""></image>
			<view class="position" v-if="WzText">
				<text>北京</text>
				<image src="@/static/icon_main_page_arrow_down.png" mode=""></image>
			</view>
			<view class="input-Box">
				<image src="@/static/icon_main_page_search.png" mode=""></image>
				<input type="text" placeholder="年度账单" />
				<image src="@/static/icon_main_page_voice.png" mode=""></image>
			</view>
			<view class="icon">
				<image src="@/static/btn_main_page_msg.png" mode=""></image>
				<image src="@/static/im_icon_add.webp" mode="" v-if="WzText" ></image>
			</view>
		</view>
	</view>
</template>

<script>
	import occupyVue from './occupy.vue';
	export default {
		name:"HomeTitle",
		data() {
			return {
				
			};
		},
		components:{
			occupyVue,
		},
		props:{
			BgColor:{
				type:String,
				default:'none'
			},
			WzText:{
				type:Boolean,
				default:true
			}
		}
	}
</script>

<style lang="scss" scoped>
	.HomeTitle{
		width: 100%;
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
	}
</style>