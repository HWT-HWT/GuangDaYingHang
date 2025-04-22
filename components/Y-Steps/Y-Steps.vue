<template>
	<!-- 获取一个数组，结构为[{date:'时间',info:'内容内容'}] -->
	<!-- @click事件返回点击标签元素的索引值 第一项为0 -->
	<view class="bg">
		<view class="steps">
			<view class="steps_item" v-for="(i, index) in infoList">
				<view class="steps_item-left">
					<text>{{i.time}}</text>
				</view>
				<view class="s_r">
					<!-- <view class="line" :style="{backgroundColor:index != 0?backgroundColor:'rgba(0,0,0,0)'}"></view> -->
					<view class="index" :style="{backgroundColor:backgroundColor,color:color}">
						
					</view>
					<view class="line" :style="{backgroundColor:'rgba(215, 215, 215,1)',paddingBottom:PadingBottom}"></view>
				</view>
				<view class="s_l">
					<view class="info_item" @tap="topage(index)">
						<view class="info_item_text"> 
							<text :style="{color:TextTitleColor,fontSize:TitleSize}" >{{ i.date }}</text>
							<view class="">
								<text>{{ i.over }} </text>
							</view>
						</view> 
						<view :style="{WebkitLineClamp:lineNum!=0?lineNum:'','color':'#888',fontSize:TextSize,}">{{ i.info }}</view>
						<view style="margin-top:10rpx;">
							{{ i.SubInfo }} <text :style="{color:SubTextColor}">{{ i.state}}</text>
						</view>
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		name: 'YSteps',
		props: {
			infoList: {
				type: Array,
				default: []
			},
			color: {
				type: String,
				default: '#fff'
			},
			backgroundColor: {
				type: String,
				default: '#ff3838'
			},
			lineNum: {
				type: [Number,String],
				default: 0
			},
			TextTitleColor:{
				type:String,
				default:'#ed8d41'
			},
			SubTextColor:{
				type:String,
				default:'#e9a655'
			},
			PadingBottom:{
				type:String,
				default:''
			},
			TitleSize:{
				 type:String,
				 default:'35rpx'
			},
			TextSize:{
				type:String,
				default:'32rpx'
			}
		},
		data() {
			return {};
		},
		onLoad(e) {
			//获取列表
		},
		methods: {
			topage(e) {
				this.$emit('click', e);
			}
		}
	};
</script>

<style lang="scss" scoped>
	page {
		background-color: #f2f2f2;
	}

	.bg {
		background-color: #fff;
		display: flex
	}

	.steps {
		display: flex;
		flex-direction: column;
		justify-content: space-between;
		width: 100%;
		padding-bottom:20rpx ;
		.steps_item {
			padding-top: 30rpx;
			display: flex;
			justify-content: space-between;
			.steps_item-left{
				display: flex;
				margin-top: 10rpx;
				font-size: 24rpx;
				color: #000;
				margin-left: 30rpx;
				display: flex;
			}
			.s_r {
				display: flex;
				flex-direction: column;
				// justify-content: center;
				align-items: center;
				.line {
					flex: 1;
					width: 4rpx;
					background-color: #fff;
				}
				.index {
					width: 15rpx;
					height: 15rpx;
					font-size: 23rpx;
					display: flex;
					justify-content: center;
					align-items: center;
					text-align: center;
					// line-height: 40rpx;
					margin: 20rpx 0;
					border-radius: 50rpx;
					// border: 2px solid #fff;
				}
			}

			.s_l {
				display: flex;
				flex-direction: column;
				.info_item {
					width: 450rpx;
					border-radius: 10upx;
					display: flex;
					flex-direction: column;
					.info_item_text{
						display: flex;
						flex-direction:row;
						// align-items: center;
						justify-content: space-between;
						text {
							// display: inline-block;
							font-size: 28rpx;
							font-weight: 500;
							color: #ea8d41;
							line-height: 25px;
							font-size: 35rpx;
							display: flex;
							align-items: center;
						}
						image{
							width: 45rpx;
							height: 45rpx;
							margin-top: 10rpx;
							margin-right: 10rpx;
						}
					}
					

					view {
						font-size: 25rpx;
						font-weight: 400;
						color: rgba(102, 102, 102, 1);
						line-height: 20px;
						overflow: hidden;
						text-overflow: ellipsis;
						display: -webkit-box;

						flex-direction: column;
					}
				}
			}
			
		}
		.steps_item-rigth{
			display: flex;
			align-items: center;
			line-height: 150rpx;
			font-size: 25rpx;
			color: #828282;
			margin: 0 20rpx;
			
		}
	}


	// .steps {
	// 	display: flex;
	// 	flex-direction: column;
	// 	margin: 0 30upx;

	// 	.steps_item {
	// 		display: flex;
	// 		align-items:center ;
	// 		background-color: #fff;
	// 		margin-top: 10rpx;
	// 		.s_r {
	// 			display: flex;
	// 			flex-direction: column;
	// 			align-items: center;
	// 			height: 100%;
	// 			background-color: #f3f;
	// 			flex: 1;
	// 			view {
	// 				height: 100%;
	// 				display: flex;
	// 				flex: 1;
	// 				height: 100%;
	// 				width: 5upx;
	// 			}

	// 			text {
	// 				display: flex;
	// 				flex-direction: column;
	// 				align-items: center;
	// 				width: 40upx;
	// 				line-height: 40upx;
	// 				height: 40upx;
	// 				border-radius: 50%;
	// 				background-color: #ff3838;
	// 				color: #ffffff;
	// 				font-size: 10px;
	// 			}
	// 		}
	// 	}
	// }

	// .info_list {
	// 	display: flex;
	// 	flex-direction: column;
	// 	flex: 1;

	// 	.info_item {
	// 		background-color: #fff;
	// 		height: 200upx;
	// 		margin: 20upx 0;
	// 		margin-right: 30upx;
	// 		border-radius: 10upx;
	// 		display: flex;
	// 		flex-direction: column;
	// 		justify-content: center;
	// 		padding: 0 30upx;

	// 		text {
	// 			font-size: 18px;
	// 			font-family: PingFangSC-Medium, PingFang SC;
	// 			font-weight: 500;
	// 			color: rgba(51, 51, 51, 1);
	// 			line-height: 25px;
	// 		}

	// 		view {
	// 			font-size: 14px;
	// 			font-family: PingFangSC-Regular, PingFang SC;
	// 			font-weight: 400;
	// 			color: rgba(102, 102, 102, 1);
	// 			line-height: 20px;
	// 			overflow: hidden;
	// 			text-overflow: ellipsis;
	// 			display: -webkit-box;
	// 			-webkit-line-clamp: 2;
	// 			flex-direction: column;
	// 		}
	// 	}

	// 	.info_item:active {
	// 		opacity: 0.6;
	// 	}
	// }
</style>
