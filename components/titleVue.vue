<template>
	<view class="Zooz-Title" :style="{'width' : width}">
		<view class="left" :style="{'fontSize' : `${LFontSize}rpx`,'fontWeight':LFontW ? 'bold':'normal','padding':Padding,'color' : Lcolor}">
			<slot name="left" ></slot>
		</view>
		<view class="rigth" :style="{'fontSize' : `${RFontSize}rpx`,'color':RColor,'fontWeight':RFontW ? 'bold':'normal'}" >
			<slot name="rigth"></slot>
			<image v-if='icon' :style="{'transform':`scale(${IconSize})`}" src="@/static/upsdk_payment_right.webp" mode=""></image>
		</view>
	</view>
</template>

<script>
	export default {
		name:"titleVue",
		data() {
			return {
				
			};
		},
		props:{
			LFontSize:{
				type:String,
				default:"30"
			},
			RFontSize:{
				type:String,
				default:"28"
			},
			LFontW:{
				type:Boolean,
				default:true
			},
			RFontW:{
				type:Boolean,
				default:false
			},
			Padding:{
				type:String,
				default:'20rpx 0rpx'
			},
			icon:{
				type:Boolean,
				default:false
			},
			RColor:{
				type:String,
				default:'#000'
			},
			Lcolor:{
				type:String,
				default:'#000'
			},
			width:{
				type:String,
				default:'100%'
			},
			IconSize:{
				type:String,
				default:'1'
			}
		},
		created() {
			
		}
	}
</script>

<style lang="scss" scoped>
	.Zooz-Title{
		width: 100%;
		display: flex;
		align-items: center;
		justify-content:space-between;
		margin: 0 auto;
		.left{
			flex: 1;
		}
		.rigth{
			font-weight: normal;
			color: #222222;
			display: flex;
			align-items: center;
			image{
				width: 30rpx;
				height: 30rpx;
				margin-left: 5rpx;
			}
		}
	}
</style>