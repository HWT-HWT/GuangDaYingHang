<template>
	<view class="ListView-box" :style="{'borderBottom': BorderBottom ? '1rpx solid #eee' :'','padding' :TBPadding}">
		<view class="name">
			<slot name="name"></slot>
			<image v-if='icon' src="@/static/right_arr2.webp" mode=""></image>
		</view>
		<view class="right-text" :style="{'color' : Rcolor}">
			<slot name="right"></slot>
			<text v-if='copy'>复制</text>
			<image v-if="RightImage" src="@/static/nine_search_right_arrow.png" mode=""></image>
		</view>
	</view>
</template>

<script>
	export default {
		name:"ListView-box",
		data() {
			return {
				
			};
		},
		props:{
			BorderBottom:{
				type:Boolean,
				default:true
			},
			icon:{
				type:Boolean,
				default:false
			},
			copy:{
				type:Boolean,
				default:false
			},
			RightImage:{
				type:Boolean,
				default:false
			},
			Rcolor:{
				type:String,
				default:'#888'
			},
			TBPadding:{
				type:String,
				default:'30rpx 20rpx'
			}
		},
		methods:{
			
		}
	}
</script>

<style lang="scss" scoped>
	.ListView-box{
		display: flex;
		justify-content: space-between;
		padding: 30rpx 20rpx;
		font-size: 30rpx;
		.name{
			display: flex;
			align-items: center;
			image{
				width: 30rpx;
				height: 30rpx;
				margin-left: 10rpx;
			}
		}
		.right-text{
			display: felx;
			align-items: center;
			text{
				margin-left: 10rpx;
				color:#4169af ;
			}
			image{
				width: 30rpx;
				height: 30rpx;
				margin-left: 10rpx;
			}
		}
	}
</style>