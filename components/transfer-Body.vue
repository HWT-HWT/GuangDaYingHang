<template>
		<view class="transfer-Body-list">
			<view class="name">
				<slot name="text"></slot>
			</view>
			
			<view class="input-text">
				{{value && input ? '￥' :''}}
				
				<textarea
				      v-if="!array.length"
				      :placeholder="placeholder"
				      :value="value"
				      rows="2"
				      placeholder-style="color: #ccc; font-weight:normal"
				      style="width: 100%; height: auto; font-size:32rpx;"
					  @input="$emit('input', $event.target.value)"
				    ></textarea>
				<view class="uni-list-cell-db" v-else >
					<picker  @change="bindPickerChange" :value="index" :range="array">
						<view class="uni-input">{{array[index]}}</view>
					</picker>
				</view>
			</view>
			
			<view class="icon">
				<image v-if="icon" :src="icon" mode="" :style="{transform: `scale(${iconSize})`}" ></image>
			</view>
			
		</view>
</template>

<script>
	export default {
		name:"transfer-Body",
		data() {
			return {
				 index: 0,
			};
		},
		props:{
			placeholder:{
				type:String
			},
			value:{
				type:String
			},
			array:{
				type:[String,Array],
			},
			input:{
				type:Boolean
			},
			icon:{
				type:String
			},
			iconSize:{
				type:String,
				default:'1'
			}
			
		},
		methods:{
			bindPickerChange: function(e) {
				// console.log('picker发送选择改变，携带值为', e.detail.value)
				this.index = e.detail.value
				uni.setStorageSync('index',e.detail.value)
			},
		},
		created() {
			// console.log(this.$props.array);
		}
	}
</script>

<style lang="scss" scoped>
		.transfer-Body-list{
			width: 96%;
			border-bottom: 1px solid #e6e6e6;
			display: flex;
			justify-content: center;
			align-items: center;
			font-size: 32rpx;
			padding: 10rpx 0;
			margin: 0 auto;
			.name{
				width: 25%;
				padding: 20rpx;
				display: flex;
				align-items: center;
			}
			
			.input-text{
				text-align: right;
				flex: 1;
				display: flex;
				align-items: center;
			}
			
			.icon{
				display: flex;
				align-items: center;
				padding:0 10rpx;
				image{
					width: 30rpx;
					height: 30rpx;
					padding: 20rpx;
				}
			}
		}
</style>