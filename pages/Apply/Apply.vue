<template>
	<view class="apply">
		<view class="transfer-title">
			<occupyVue hight="90rpx"></occupyVue>
			<backtaberVue  :TitleImage='TitleImage' :rigthIcon="rigthIcon" IconHeight="45rpx" IconWidth="45rpx" Padding="0 30rpx">
				申请进度
			</backtaberVue>
		</view>
		
		<view class="apply-image">
			<image src="@/static/apply-image-1.png" mode=""></image>
			<span>您暂无申请记录</span>
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
				rigthIcon:[{icon:'../../static/info_details_icon_click_more.png'}],
			};
		},
		components:{
			occupyVue,
			backtaberVue,
		},
	}
</script>

<style lang="scss">
	.apply{
		width: 100vw;
		height: 100vh;
		background-color: #f8f8f8;
		.transfer-title{
			background-color: #fff;
		}
		.apply-image{
			display: flex;
			align-items: center;
			justify-content: center;
			margin-top: 200rpx;
			flex-wrap: wrap;
			image{
				width: 380rpx;
				height: 300rpx;
			}
			span{
				width: 100%;
				color: #b9b9b9;
				font-size: 28rpx;
				text-align: center;
				margin-top: 20rpx;
			}
		}
	}
</style>
