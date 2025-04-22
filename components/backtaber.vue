<template>
	<view class="pension-backtaber" :style="{width:BigWidth}">
		<occupyVue></occupyVue>
		<view class="backtaber-box">
			<view class="backtaber-title" :style="{color:Color}">
				<slot></slot>
			</view>
		
		</view>
		
		<view class="backtaber-icon">
			<view>
				<image :src="TitleImage" mode="" @click="back"></image>
			</view>
			<view class="backtaber-right-icon" >
				<view class="right-icon-box" v-for="(item,index) in rigthIcon" :key="index" @click="ClickIcon(index)">
					<image :src="item.icon" mode="" :style="{width:IconWidth,height:IconHeight,padding:Padding}"></image>
					<span v-if="item.name">{{item.name}}</span>
				</view>
			</view>
			
		</view>
	</view>
</template>

<script>
	import occupyVue from './occupy.vue';
	export default {
		name:"backtaber",
		data() {
			return {
				
			};
		},
		props:{
			TitleImage:{
				type:String
			},
			rigthIcon:{
				type:Array,
			},
			RightMax:{
				type:Number,
				default:1.8
			},
			isText:{
				type:Boolean,
				default:false
			},
			rightText:{
				type:String,
				default:'30'
			},
			Color:{
				type:String,
				default:'#000'
			},
			IconWidth:{
				type:String,
				default:'40rpx'
			},
			IconHeight:{
				type:String,
				default:'40rpx'
			},
			Padding:{
				type:String,
				default:'0'
			},
			BigWidth:{
				type:String,
				default:'100vw'
			}
		},
		methods:{
			back(){
				uni.navigateBack()
			},
			ClickIcon(index){
				this.$emit('GetIndex',index)
			}
		},
		components:{
			occupyVue
		}
	}
</script>

<style lang="scss" scoped>
	.pension-backtaber{
		margin: 0 auto;
		padding-bottom: 20rpx;
		.backtaber-box{
			display: flex;
			align-items: center;
			justify-content: center;
			.backtaber-title{
				font-size: 40rpx;
			}
			
		}
		.backtaber-icon{
			width: 100%;
			margin: 0 auto;
			display: flex;
			align-items: center;
			justify-content: space-between;
			position: absolute;
			top: 95rpx;
			image{
				width: 45rpx;
				height: 45rpx;
				padding:  0 20rpx;
			}
			.backtaber-right-icon{
				display: flex;
				.right-icon-box{
					display: flex;
					flex-wrap: wrap;
					justify-content: center;
					margin-top: -5rpx;
					image{
						width: 40rpx;
						height: 40rpx;
					}
					span{
						text-align: center;
						font-size: 22rpx;
						width: 100%;
					}
				}
				
			}
		}
	}
</style>