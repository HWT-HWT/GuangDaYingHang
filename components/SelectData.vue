<template>
	<view class="SelectData">
		<view class="uni-padding-wrap">
			<view class="uni-title" @click="toggle('bottom')" >{{year}}-{{month < 10 ? '0' + month : month}}</view>
		</view>
		
		<uni-popup ref="popup" background-color="#fff" @change="change">
			
			<view class="Title">
				<view class="Account-tabs">
					  <z-tabs ref="tabs" :list="tabList" :current="current" @change="tabsChange" :bar-style="{background:'#7d38d1'}" :active-style='{color:"#7647b0"}' :tabs-style='{height:"100rpx"}' />
				</view>
				<image @click="close" src="@/static/ic_close.png" mode=""></image>
			</view>
			
			<view class="popup-content" :class="{ 'popup-height': type === 'left' || type === 'right' }">
				<picker-view v-if="visible" :indicator-style="indicatorStyle" :value="valueData" @change="bindChange" class="picker-view">
				    <picker-view-column>
				        <view class="item" v-for="(item,index) in years" :key="index">{{item}}年</view>
				    </picker-view-column>
				    <picker-view-column>
				        <view class="item" v-for="(item,index) in months" :key="index">{{item}}月</view>
				    </picker-view-column>
				   <!-- <picker-view-column>
				        <view class="item" v-for="(item,index) in days" :key="index">{{item}}日</view>
				    </picker-view-column> -->
				</picker-view>
			</view>
			
			<view class="btn" @click="Right">
				确定
			</view>
		</uni-popup>
	</view>
</template>

<script>
	export default {
		data: function () {
			const date = new Date()
			const years = []
			const year = date.getFullYear()
			const months = []
			const month = date.getMonth() + 1
			const days = []
			const day = date.getDate()
			for (let i = 1990; i <= date.getFullYear(); i++) {
				years.push(i)
			}
			for (let i = 1; i <= 12; i++) {
				months.push(i)
			}
			for (let i = 1; i <= 31; i++) {
				days.push(i)
			}
			return {
				years,
				year,
				months,
				month,
				days,
				day,
				valueData: [9999, month - 1, day - 1],
				visible: true,
				indicatorStyle: `height: 50px;`,
				type: 'center',
				msgType: 'success',
				messageText: '这是一条成功提示',
				value: '',
				tabList: ['选择月份','自定义'],
				current:0
			}
		},
		methods: {
			bindChange: function (e) {
				const val = e.detail.value
				this.year = this.years[val[0]]
				this.month = this.months[val[1]]
				this.day = this.days[val[2]]
			},
			// 检测时间选择器状态 打开为 true 关闭 false
			change(e) {
				console.log('当前模式：' + e.type + ',状态：' + e.show);
			},
			
			// 打开弹出层
			toggle(type) {
				this.type = type
				this.$refs.popup.open(type)
			},
			// 关闭弹出层
			Right(){
				this.$refs.popup.close()
			},
			tabsChange(index){
				this.current = index
			},
			close(){
				this.$refs.popup.close()
			}
		},
		props:{
				StartedEnd:{
					type:Number
				},
		},
		components:{
			
		},
	}
</script>

<style lang="scss" scoped>
	.SelectData{
		.Title{
			display: flex;
			align-items: center;
			border: bottom 1px solid #ddd;
			justify-content: space-between;
			.Account-tabs{
				width: 90%;
			}
			image{
				padding: 20rpx;
				width: 50rpx;
				height: 50rpx;
			}
		}
		.btn{
			width: 95%;
			padding: 20rpx 0;
			margin: 0 auto;
			font-size: 35rpx;
			text-align: center;
			background-color: #7d38d1;
			border-radius: 10rpx;
			color: #fff;
			margin-bottom: 20rpx;
		}
	}
	
	.picker-view {
		width: 750rpx;
		height: 600rpx;
		margin-top: 20rpx;
	}
	.item {
		line-height: 100rpx;
		text-align: center;
	}
	.popup-Top-Btn{
		padding: 20rpx;
		font-size: 28rpx;
		display: flex;
		align-items: center;
		justify-content: space-between;
		span{
			color: dodgerblue;
		}
	}
</style>