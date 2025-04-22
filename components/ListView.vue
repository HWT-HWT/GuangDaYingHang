<template>
	<view class="index-listTitle" :style="{'background':BgColor}">
		<view class="listTitle" v-for="(item,index) in listTitle" :key="index" :style="{'padding' :Pad, width:width}" @click="GetIndex(index)">
			<image :src="item.icon" :style="{'width':sizi,'height':sizi}" mode=""></image>
			<view class="listTitle-lade" :style="{'fontSize':FontSize,height:TextHeight}">{{item.name}}</view>
		</view>
	</view>
</template>

<script>
	export default {
		name:"ListView",
		data() {
			return {
				
			};
		},
		props:{
			listTitle:{
				type:[Object,Array]
			},
			sizi:{
				type:String,
				default:'70rpx'
			},
			BgColor:{
				type:String,
				default:'none'
			},
			FontSize:{
				type: String,
				default:'28rpx'
			},
			Pad:{
				type: String,
				default:'10rpx 0'
			},
			width:{
				type: String,
				default:'20%'
			},
			TextHeight:{
				type: String,
			}
		},
		methods:{
			GetIndex(index){
				this.$emit('GetIndex',index)
			}
		}
	}
</script>

<style lang="scss" scoped>
	.index-listTitle{
		display: flex;
		width: 100%;
		margin: 0 auto;
		justify-content: space-between;
		flex-wrap: wrap;
		border-radius: 30rpx;
		z-index: 998;
		.listTitle{
			width: 20%;
			display: flex;
			flex-wrap: wrap;
			align-items: center;
			justify-content: center;
			.listTitle-lade{
				// height: 50rpx;
				font-size: 25rpx;
				width: 100%;
				text-align: center;
				margin-top: 10rpx;
			}
		}
	}
</style>