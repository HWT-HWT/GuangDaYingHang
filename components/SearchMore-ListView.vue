<template>
	<view class="SearchMore-ListView">
		<text :style="{color:color}"><slot name="name"></slot></text>
		<p><slot name="style"></slot></p>
		<!-- <image v-if='icon' src="@/static/nine_search_right_arrow.png" mode=""></image>
		<text v-else><slot name="rightText"></slot></text> -->
	</view>
</template>

<script>
	export default {
		name:"SearchMore-ListView",
		data() {
			return {
				
			};
		},
		props:{
			color:{
				type:String,
				default:'#888'
			},
			icon:{
				type:Boolean,
				default:true
			}
		}
	}
</script>

<style lang="scss" scoped>
	.SearchMore-ListView{
		display: flex;
		align-items: center;
		justify-content: space-between;
		background-color: #fff;
		// padding: 25rpx;
		p{
			// color: #2764d4;
			flex: 1;
			// padding: 0 80rpx;
		}
		image{
			width: 30rpx;
			height: 30rpx;
		}
	}
</style>