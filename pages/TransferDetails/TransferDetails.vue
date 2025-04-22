<template>
	<view class="TransferDetails">
		<view class="transfer-title">
			<occupyVue hight="90rpx"></occupyVue>
			<backtaberVue  :TitleImage='TitleImage' :rigthIcon="rigthIcon" IconHeight="45rpx" IconWidth="45rpx" Padding="0 30rpx">
				转账明细查询
			</backtaberVue>
		</view>
		<view class="transfer-Search">
			<view class="Search-box">
				<image src="../../static/icon_main_page_search.png" mode=""></image>
				<span>请输入收款人姓名/卡号</span>
			</view>
		</view>
		<view class="Details-SelectTabs">
			<view class="Tabs" @click="popup(0)">
				{{AccountName}} <image src="../../static/upsdk_card_arrow_right.webp" mode=""></image>
			</view>
			<view class="Tabs" @click="popup(1)">
				{{transfer}} <image src="../../static/upsdk_card_arrow_right.webp" mode=""></image>
			</view>
			<view class="Tabs" @click="popup(2)">
				{{Time}} <image src="../../static/upsdk_card_arrow_right.webp" mode=""></image>
			</view>
		</view>
		<view class="TransferDetails-date">
			<view class="date">
				<span>查询范围</span>
				<span>2025/02/19-2025/03/19</span>
			</view>
		</view>
		<view class="TransferDetails-text">
			该时间段内无查询记录
		</view>
		<view class="OtherCards-tisi">
			<p>温馨提示:</p>
			<span>您可查询1年内通过手机银行办理的转账明细。</span> <br>
		</view>
		
		<uni-popup ref="popup" background-color="#f8f8f8" @change="change" :borderRadius='"20px 20px 0px 0px"'>
			<view class="Account-title">
				<span>请选择账户</span>
				<image src="@/static/ic_close.png" mode=""></image>
			</view>
			<view class="Account-ListView">
				全部账户
			</view>
			<view class="Account-ListView">
				622663********0436/阳光卡
			</view>
		</uni-popup>
		
		<uni-popup ref="Account" background-color="#f8f8f8" @change="change" :borderRadius='"20px 20px 0px 0px"'>
			<view class="Account-title">
				<span>请选择账户</span>
				<image src="@/static/ic_close.png" mode=""></image>
			</view>
			<view class="Account-ListView" v-for="(item,index) in Account" :key="index" :style="{color: index === subscript ? '#793fbf': '#888'}" @click="GetIndex(index,item,1)">
				{{item}} <image src="@/static/icon_account_check-1.png" v-if="index === subscript"></image>
			</view>
		</uni-popup>
		
		<uni-popup ref="popup" background-color="#f8f8f8" @change="change" :borderRadius='"20px 20px 0px 0px"'>
			<view class="Account-title">
				<span>请选择账户</span>
				<image src="@/static/ic_close.png" mode=""></image>
			</view>
			<view class="Account-ListView" v-for="(item,index) in popupName" :key="index" :style="{color: index === subscript ? '#793fbf': '#888'}" @click="GetIndex(index,item,2)">
				{{item}} <image src="@/static/icon_account_check-1.png" v-if="index === subscript"></image>
			</view>
		</uni-popup>
		
		<uni-popup ref="Time" background-color="#fff" @change="change" :borderRadius='"20px 20px 0px 0px"'>
			<view class="Account-title">
				<span>请选择时间</span>
				<image src="@/static/ic_close.png" mode=""></image>
			</view>
			<view class="Time-content">
				<titleVue Padding="20rpx" :LFontW="false">
					<template #left>
						交易时间
					</template>
				</titleVue>
				<view class="ListView" >
					<view class="Box" v-for="(item,index) in time" :key="index" @click="GetTime(item)">
						{{item}}
					</view>
				</view>
			</view>
			
			<view class="Time-content">
				<titleVue Padding="20rpx" :LFontW="false">
					<template #left>
						交易时间 <text style="font-size: 22rpx; margin-left: 10rpx; color: #888;">(您可查询1年内通过手机银行办理的转账明细)</text>
					</template>
				</titleVue>
				<view class="Time-Select">
					<view class="Select">
						起始时间
					</view>
					<view class="Select">
						结束时间
					</view>
				</view>
			</view>
		</uni-popup>
	</view>
</template>

<script>
	import occupyVue from '../../components/occupy.vue'
	import backtaberVue from '../../components/backtaber.vue'
	import titleVue from '../../components/titleVue.vue';
	export default {
		data() {
			return {
				TitleImage:'../../static/ic_black_left_back.png',
				rigthIcon:[{icon:'../../static/info_details_icon_click_more.png'}],
				time:['近一周','近一个月','近三个月','近半年','近一年'],
				popupName:['全部','转账汇款','从他行汇款'],
				Account:['全部账户','622663********0436/阳光卡'],
				AccountName:'全部账号',
				transfer:'转账汇款',
				Time:'近一个月',
				subscript:0
			};
		},
		components:{
			occupyVue,
			backtaberVue,
			titleVue
		},
		methods:{
			change(e) {
				console.log('当前模式：' + e.type + ',状态：' + e.show);
			},
			popup(index){
				console.log(index);
				// this.$refs.popup.open('bottom')
				index === 0 ? this.$refs.Account.open('bottom') : ''
				index === 1 ? this.$refs.popup.open('bottom') : ''
				index === 2 ? this.$refs.Time.open('bottom') : ''
			},
			GetTime(name){
				console.log(name);
				this.Time = name
				this.$refs.Time.close()
			},
			GetIndex(index,name,Lenght){
				console.log(index);
				console.log(name.length);
				Lenght === 1 ? this.AccountName = name : this.transfer = name
				if(Lenght === 1){
					name.length > 4 ? this.AccountName = '阳光卡(0436)' : ''
				}
				this.subscript = index
				this.$refs.Account.close()
				this.$refs.popup.close()
				
			}
		}
	}
</script>

<style lang="scss">
	.TransferDetails{
		width: 100vw;
		height: 100vh;
		background: #f8f8f8;
		.transfer-title{
			background-color: #fff;
		}
		.transfer-Search{
			background-color: #fff;
			padding: 30rpx;
			.Search-box{
				display: flex;
				align-items: center;
				width: 95%;
				margin: 0 auto;
				background-color: #f5f5f5;
				border-radius: 50rpx;
				image{
					padding:10rpx 20rpx;
					width: 35rpx;
					height: 35rpx;
				}
				span{
					font-size: 28rpx;
					color: #555;
				}
			}
			
		}
		.Details-SelectTabs{
			padding:0rpx 30rpx;
			background-color: #fff;
			display: flex;
			align-items: center;
			justify-content: space-between;
			border-bottom: 1px solid #eaeaea;
			.Tabs{
				width: 30%;
				white-space: nowrap;    
				overflow: hidden;           /* 隐藏溢出内容 */
				text-overflow: ellipsis; 
				font-size: 28rpx;
				color: #555;
				display: flex;
				justify-content: center;
				align-items: center;
				padding: 20rpx;
				image{
					width: 20rpx;
					height: 20rpx;
					margin-left: 10rpx;
				}
			}
			.Tabs:hover{
				color: #2e339c;
			}
		}
		.TransferDetails-date{
			width: 100%;
			.date{
				display: flex;
				align-items: center;
				justify-content: space-between;
				width: 90%;
				margin: 0 auto;
				font-size: 30rpx;
				color: #555;
				border-bottom: 1px solid #eaeaea;
				padding: 20rpx ;
			}
		}
		.TransferDetails-text{
			margin: 0 auto;
			padding: 40rpx;
			background-color: #fff;
			font-weight: bold;
			margin-top: 10rpx;
		}
		.OtherCards-tisi{
			width: 90%;
			margin: 0 auto;
			margin-top: 50rpx;
			position: absolute;
			bottom: 50rpx;
			left: 50rpx;
			p{
				color: #fd8d0a;
				font-weight: bold;
			}
			span{
				font-size: 25rpx;
				color: #888;
			}
		}
		.Account-title{
			display: flex;
			align-items: center;
			justify-content: space-between;
			padding: 20rpx;
			border-bottom: 1px solid #ddd;
			span{
				width: 100%;
				font-size: 35rpx;
				text-align: center;
			}
			image{
				width: 50rpx;
				height: 50rpx;
			}
		}
		.Account-ListView{
			padding: 30rpx;
			display: flex;
			justify-content: space-between;
			image{
				width: 20rpx;
				height: 20rpx;
			}
		}
		.Time-content{
			.ListView{
				padding: 0 20rpx;
				display: flex;
				flex-wrap: wrap;
				// justify-content: space-between;
				.Box{
					width: 30%;
					text-align: center;
					border: 1px solid #ddd;
					background-color: #f8f8f8;
					padding: 10rpx 0;
					border-radius: 10rpx;
					font-size: 28rpx;
					color: #555;
					margin-bottom: 20rpx;
					margin-right: 20rpx;
				}
				.Box:hover{
					color: #743fb4;
					border: 1px solid #7c59a4;
				}
				
			}
			.Time-Select{
				width: 95%;
				margin: 0 auto;
				display: flex;
				justify-content: space-between;
				padding-bottom: 100rpx;
				.Select{
					text-align: center;
					width:  35%;
					padding:10rpx 40rpx;
					background-color: #f8f8f8;
					border-radius: 10rpx;
					color: #666;
				}
			}
		}
	}
</style>
