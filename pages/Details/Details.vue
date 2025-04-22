<template>
	<view class="Details">
		<view class="Details-title">
			<occupyVue hight="90rpx"></occupyVue>
			<backtaberVue  :TitleImage='TitleImage' :rigthIcon="rigthIcon" @ClickIcon='GetIndex'>
				交易明细
			</backtaberVue>
		</view>
		<view class="Details-list">
			<span>账户</span>
			<view class="list-box" @click="OpenSelectAccount()">
				<span>622663*******0436</span>
				<image src="../../static/arraw_right.webp" mode=""></image>
			</view>
		</view>
		<view class="Details-SelectTabs">
			<view class="Tabs">
				<SearchMoreListViewVue>
					<template #style>
						<SelectDataVue @Date="Data" :StartedEnd='0'></SelectDataVue>
					</template>
				</SearchMoreListViewVue>
				<image src="@/static/upsdk_card_arrow_right.webp" mode=""></image>
			</view>
			<view class="Tabs" @click="OpenView(1)">
				{{MoneyType}} <image src="../../static/upsdk_card_arrow_right.webp" mode=""></image>
			</view>
			<view class="Tabs" @click="OpenView(2)">
				筛选 <image src="../../static/upsdk_card_arrow_right.webp" mode=""></image>
			</view>
		</view>
		<view class="Details-Datails" v-for="(item,index) in DetailsList" :key="index">
			<p>{{item.time}}</p>
			<view class="Datails-Text">
				<text>支出 <span class="color">￥{{item.zhichu}}</span> </text>
				<text>收入 <span>￥{{item.shouru}}</span> </text>
			</view>
			
			<view class="List-View" v-for="(sum,num) in item.list" :key="num" @click="GoLoanDatali(item.list,num)">
				<view class="View-box">
					<span>{{sum.name}}</span>
					<text>{{sum.time}}</text>
				</view>
				<view class="View-box-right">
					<view class="Box" :style="{color: !sum.IsTure ? '#cb5a31' : '#14b570'}">
						<view class="Box-title">
							{{!sum.IsTure ? '收入' : '支出'}}
						</view>
						<span>{{sum.money}}</span>
					</view>
					<text>余额:￥{{sum.balance}}</text>
				</view>
			</view>
		</view>
		
		<view class="Details-Menu" @click="add(DetailsList[M].id)" v-if="DetailsList.length !== 15">
			<image style="transform: scale(-1);" src="@/static/upsdk_card_arrow_right.webp" mode=""></image>
			 <span>点击加载更多</span>
		</view>
		
		<uni-popup ref="popup" background-color="#f8f8f8" :borderRadius='"20px 20px 20px 20px"'>
			<view class="Popup" v-for="(item,index) in Popup" :key="item" :style="{borderRadius: index === 0 ? '40rpx 40rpx 0 0' : '0 0'}" @click="GoUrl(item)">
				{{item}}
			</view>
			<view class="Popup-image" >
				<image @click="close" src="@/static/ic_close.png" mode=""></image>
			</view>
		</uni-popup>
		
		<uni-popup ref="Selsect" background-color="#f8f8f8" :borderRadius='"20px 20px 0px 0px"'>
			<view class="Selsect-title">
				<span>请选择筛选条件</span>
				<image @click="close()" src="@/static/ic_close.png" mode=""></image>
			</view>
			
			<view class="Selsect-content">
				<view class="ListView">
					<titleVue LFontSize="30">
						<template #left>
							收支方向
						</template>
					</titleVue>
					<view class="contet" v-for="(item,index) in SelsectContent" :key="index" :style="{border:index === Selsect ? '1px solid #7d38d1':'1px solid #ddd' ,color:index === Selsect ? '#7d38d1':'#000'}" @click="GetIndex(index)">
						{{item}}
						<view class="image" v-if="index == Selsect">
							<image src="@/static/icon_account_check.png" mode=""></image>
						</view>
					</view>
				</view>
				
				<view class="ListView">
					<titleVue LFontSize="30">
						<template #left>
							交易金额
						</template>
					</titleVue>
					<view class="Select" v-for="(item,index) in money" :key="index" @click="GetYes(index)">
						<view class="checkbox">
							<image v-if="index === Yes" src="@/static/icon_account_check-1.png" mode=""></image>
						</view>
						<span>{{item}}</span>
					</view>
					
					<view class="Select-Input">
						<view class="input-Box">
							￥最低金额
						</view>
						—
						<view class="input-Box">
							￥最高金额
						</view>
					</view>
				</view>
				
				<view class="ListView">
					<titleVue LFontSize="30">
						<template #left>
							交易对手
						</template>
					</titleVue>
					<view class="text">
						请输入交易对手名称
					</view>
				</view>
				
				<view class="btn" @click="close">
					确定
				</view>
			</view>
		</uni-popup>
		
		<uni-popup ref="SelectAccount" background-color="#f8f8f8" :borderRadius='"20px 20px 0px 0px"'>
			<view class="SelectAccount">
				<view class="Popup">
					选择账户
				</view>
				<view class="SelectAccount-ListView">
					<view class="">
						<image src="@/static/face_pay_item_logo.webp" mode=""></image>
						<span>622663******0436 / 借记卡</span>
					</view>
					<image class="Select" src="@/static/ic_choosed.png" mode=""></image>
				</view>
				<view class="SelectAccount-ListView">
					<view class="">
						<image src="@/static/face_pay_item_logo.webp" mode=""></image>
						<span>信用卡账户查询</span>
					</view>
					<view style="width: 25rpx; height: 25rpx; border-radius: 50rpx; border: 1px solid #888;">
						
					</view>
				</view>
				<view class="Popup-image" >
					<image @click="close" src="@/static/ic_close.png" mode=""></image>
				</view>
			</view>
		</uni-popup>
		
	</view>
</template>

<script>
	import occupyVue from '../../components/occupy.vue'
	import backtaberVue from '../../components/backtaber.vue'
	import SearchMoreListViewVue from '@/components/SearchMore-ListView.vue'
	import SelectDataVue from '@/components/SelectData.vue'
	import titleVue from '../../components/titleVue.vue'
	export default {
		data() {
			return {
				TitleImage:'../../static/ic_black_left_back.png',
				rigthIcon:[
					{name:'搜索',icon:'../../static/title-icon-1.png'},
					{name:'电子证明',icon:'../../static/title-icon-2.png'},
				],
				Tabs:[''],
				Popup:['币种','人民币','美元','日元','港币','英镑'],
				type:"",
				MoneyType:'人民币',
				SelsectContent:['全部收入','收入','支出'],
				DetailsList:[
					{
						id:4,
						time:`2025年04月`,
						zhichu:'0.00',
						shouru:'0.00',
					},
				],
				Selsect:0,
				money:['0-5万','5-10万','10万以上','自定义金额'],
				Yes:'',
				M:0
			}
		},
		methods: {
			Data({time}){
				console.log(time);
			},
			OpenView(index){
				if(index === 1){
					this.type = 'bottom'
					this.$refs.popup.open('bottom')
				}
				if(index === 2){
					this.$refs.Selsect.open('bottom')
				}
				
			},
			GoUrl(item){
				item == '币种' ? '人民币' : this.MoneyType = item
				this.$refs.popup.close()
			},
			close(){
				this.$refs.popup.close()
				this.$refs.Selsect.close()
				this.$refs.SelectAccount.close()
			},
			add(id){
				let ListId = id - 1
				if(this.DetailsList.length === 9){
					return 
				}
				if(ListId <= 0){
					ListId = 12
				}
				this.M++
				console.log(ListId);
				if(ListId === 3 || 2 || 1 || 12 || 11 || 10 || 9 || 8){
					let list = {
						id:ListId,
						time:`202${this.DetailsList.length+1 > this.DetailsList[0].id ? '4': '5' }年${ListId<10 ? '0' + ListId : ListId}月`,
						zhichu:'0.00',
						shouru:'0.00',
						list:[
							{
								arr:['622663******0436',`202${this.DetailsList.length+1 > this.DetailsList[0].id ? '4': '5' }-${ListId<10 ? '0' + ListId : ListId}-20 22:04:17`,'人民币','批处理归还欠款-388824770001RH001','388801*******0099','-'],
								name:'其他个人贷款利息收入',
								time:`${ListId<10 ? '0' + ListId : ListId}-20 22:04`,money:'2,666.50',
								IsTure:true,
								balance:'0.00',
							},
						],
					}
					this.DetailsList.push(list)
				}else{
					let list = {
						id:ListId,
						time:`202${this.DetailsList.length+1 > this.DetailsList[0].id ? '4': '5' }年${ListId<10 ? '0' + ListId : ListId}月`,
						zhichu:'0.00',
						shouru:'0.00',
					}
					this.DetailsList.push(list)
				}
			},
			GoLoanDatali(obj,index){
				uni.setStorageSync('Detali',obj[index])
				uni.navigateTo({
					url:'/pages/TransferDetalis-Detalis/TransferDetalis-Detalis'
				})
			},
			GetIndex(index){
				this.Selsect = index
			},
			GetYes(index){
				this.Yes = index
			},
			OpenSelectAccount(){
				this.$refs.SelectAccount.open('bottom')
			}
		},
		components:{
			backtaberVue,
			occupyVue,
			SearchMoreListViewVue,
			SelectDataVue,
			titleVue
		}
	}
</script>

<style lang="scss" scoped>
	.Details{
		width: 100vw;
		min-height: 100vh;
		background-color: #f8f8f8;
		padding-bottom: 50rpx;
		.Details-title{
			background-color: #fff;
			position: fixed;
			top: 0;
			z-index: 999;
			.Title{
				display: flex;
				flex-wrap:wrap;
				align-items: center;
				justify-content: space-between;
			}
		}
		.Details-list{
			background-color: #fff;
			padding:30rpx;
			margin: 0 auto;
			display: flex;
			justify-content: space-between;
			font-size: 32rpx;
			border-bottom: 1px solid #ddd;
			margin-top: 160rpx;
			.list-box{
				display: flex;
				align-items: center;
				image{
					width: 35rpx;
					height: 35rpx;
					margin: 0 10rpx;
				}
			}
		}
		.Details-SelectTabs{
			background-color: #fff;
			display: flex;
			align-items: center;
			justify-content: space-between;
			.Tabs{
				font-size: 28rpx;
				color: #9f9f9f;
				padding: 20rpx;
				display: flex;
				align-items: center;
				image{
					width: 25rpx;
					height: 25rpx;
					margin-left: 10rpx;
				}
			}
		}
		.Details-Datails{
			margin: 0 auto;
			line-height: 50rpx;
			margin-top: 20rpx;
			p{
				padding: 0 20rpx;
				font-size: 32rpx;
			}
			.Datails-Text{
				padding: 0 20rpx;
				font-size: 30rpx;
				text{
					margin-right: 30rpx;
					span{
						font-size: 32rpx;
						color: #b86f50;
					}
					.color{
						color: #3fb084;
					}
				}
			}
			.List-View{
				background-color: #fff;
				padding: 20rpx;
				border-bottom:1px solid #ddd;
				display: flex;
				justify-content: space-between;
				.View-box{
					display: flex;
					flex-wrap: wrap;
					span{
						font-size: 30rpx;
						width: 100%;
					}
					text{
						font-size: 25rpx;
						color: #888;
					}
				}
				.View-box-right{
					display: flex;
					flex-wrap: wrap;
					text-align: right;
					padding-right: 20rpx;
					.Box{
						width: 100%;
						display: flex;
						align-items: center;
						justify-content: right;
						.Box-title{
							display: flex;
							align-items: center;
							justify-content: center;
							width: 60rpx;
							height: 30rpx;
							border-radius: 50rpx;
							border: 1px solid;
							font-size: 18rpx;
						}
						span{
							font-size: 35rpx;
							margin-left: 10rpx;
						}
					}
					
					text{
						width: 100%;
						font-size: 25rpx;
						color: #888;
					}
				}
			}
		}
		.SelectAccount{
			.Popup{
				display: flex;
				justify-content: center;
				align-items: center;
				padding: 30rpx;
				border-bottom: 1px solid #ebebeb;
				font-size: 28rpx;
				background-color: #fff;
			}
			.SelectAccount-ListView{
				background-color: #fff;
				padding: 20rpx;
				display: flex;
				align-items: center;
				justify-content: space-between;
				border-bottom: 1px solid #ddd;
				view{
					display: flex;
					align-items: center;
					image{
						width: 80rpx;
						height: 80rpx;
						margin-right: 10rpx;
					}
					span{
						font-size: 28rpx
					}
				}
				
				.Select{
					width: 30rpx;
					height: 30rpx;
				}
			}
			.Popup-image{
				position: absolute;
				z-index: 999;
				top: 25rpx;
				left: 20rpx;
				image{
					z-index: 999;
					width: 40rpx;
					height: 40rpx;
				}
			}
		}
		.Popup{
			display: flex;
			justify-content: center;
			align-items: center;
			padding: 30rpx;
			border-bottom: 1px solid #ebebeb;
			font-size: 32rpx;
			background-color: #fff;
		}
		.Popup-image{
			position: absolute;
			z-index: 999;
			top: 25rpx;
			left: 20rpx;
			image{
				z-index: 999;
				width: 50rpx;
				height: 50rpx;
			}
		}
		.Popup-btn{
			text-align: center;
			padding: 30rpx;
			margin-top: 20rpx;
			color: #7c47be;
			font-size: 32rpx;
			background-color: #fff;
		}
		.Selsect-title{
			display: flex;
			justify-content: space-between;
			padding: 20rpx;
			span{
				font-weight: bold;
				flex: 1;
				font-size: 35rpx;
				text-align: center;
			}
			image{
				width: 50rpx;
				height: 50rpx;
			}
		}
		.Selsect-content{
			padding: 20rpx;
			.ListView{
				display: flex;
				flex-wrap: wrap;
				justify-content: space-between;
				flex-wrap: wrap;
				.contet{
					width: 30%;
					position: relative;
					border: 1px solid;
					font-size: 24rpx;
					border-radius: 10rpx;
					color: #7d38d1;
					text-align: center;
					padding: 10rpx 0;
					.image{
						width: 30rpx;
						height: 30rpx;
						position: absolute;
						bottom: 0rpx;
						right: 0;
						border-radius: 100rpx 5rpx 5rpx 5rpx;
						background-color: #7d38d1;
						display: flex;
						justify-content: center;
						align-items: center;
						image{
							width: 15rpx;
							height: 15rpx;
							margin-left: 5rpx;
							margin-top: 5rpx;
						}
					}
				}
				.Select{
					width: 30%;
					display: flex;
					align-items: center;
					margin-bottom: 20rpx;
					.checkbox{
						width: 30rpx;
						height: 30rpx;
						border: 1px solid #888;
						border-radius: 20rpx;
						margin-right: 10rpx;
						image{
							width: 40rpx;
							height: 40rpx;	
							position: relative;
							top: -10rpx;
						}
					}
				}
				.Select-Input{
					width: 100%;
					display: flex;
					justify-content: space-between;
					align-items: center;
					color: #999;
					.input-Box{
						display: flex;
						align-items: center;
						border-radius: 10rpx;
						width: 300rpx;
						background-color: #ddd;
						height: 80rpx;
						font-size: 28rpx;
						padding-left: 20rpx;
					}
				}
				.text{
					width: 100%;
					padding: 20rpx;
					background-color: #ddd;
					font-size: 25rpx;
					border-radius: 10rpx;
					color: #888;
				}
			}
			.btn{
				width: 100%;
				margin: 0 auto;
				background-color: #7d38d1;
				padding:20rpx 0;
				display: flex;
				justify-content: center;
				color: #fff;
				border-radius: 10rpx;
				margin-top: 50rpx;
			}
		}
		.Details-Menu{
			width: 100%;
			display: flex;
			align-items: center;
			justify-content: center;
			margin-top: 50rpx;
			image{
				width: 40rpx;
				height: 40rpx;
			}
			span{
				font-size: 30rpx;
				color: #888;
				margin-left: 10rpx;
			}
		}
	}
</style>
