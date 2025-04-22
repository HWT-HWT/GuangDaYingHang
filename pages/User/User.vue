<template>
	<view class="User">
		<view class="User-Title">
			<occupyVue hight="80rpx"></occupyVue>
			<view class="User-Quit" @click="Quit">
				<image src="@/static/btn_main_page_exit.png" mode=""></image>
				安全退出
			</view>
			<view class="User-Menu">
				<image src="@/static/icon_main_page_search.png" mode=""></image>
				<image src="@/static/btn_main_page_setting.png" mode=""></image>
				<view class="gif">
					<image src="@/static/btn_main_page_help.gif" mode=""></image>
				</view>
				<image src="@/static/im_icon_add.webp" mode=""></image>
			</view>
		</view>
		<view class="User-HeadBox">
			<view class="Head-Name">
				<image src="@/static/icon_mine_head.png" mode=""></image>
				<view class="Headt-List">
					<p>*静女士,中午好!</p>
					<image src="@/static/icon_customer_normal.png" mode=""></image>
				</view>
			</view>
			<image src="@/static/user-bg-4.png" mode=""></image>
		</view>
		<view class="User-ListView">
			<view class="ListView">
				<view class="Text" v-for="(item,index) in ListViewText" :key="index">
					<p>{{item.text}}</p>
					<span>{{item.subtitle}}</span>
				</view>
			</view>
			<view class="ListView-btn">
				<ListViewVue :listTitle='ListViewList' Pad="0rpx 0" width="25%" ></ListViewVue>
			</view>
		</view>
		<view class="User-notice">
			<view class="notice-text">
				<image src="@/static/home_scroll_jj.png" mode=""></image>
				<text>聚焦</text>
				<p>【晚报】创近4个月新高！人民币继续…</p>
			</view>
			
			<image src="@/static/upsdk_payment_right.webp" mode=""></image>
		</view>
		<view class="User-property">
			<view class="property-title">
				<view class="left" @click="SetEye">
					我的资产(元) 
					<image v-if="!UserEye" src="../../static/xwr_wealth_my_wallet_eye_close.png" mode=""></image>
					<image v-else src="../../static/xwr_wealth_my_wallet_eye_open.png" mode=""></image>
				</view>
				<view class="right">日收益(元) <image src="@/static/icon_number_helper_help_cherryblossom.png" mode=""></image> :<span>{{ UserEye ? '0.00' : '*******'}}</span>	</view>
			</view>
			<view class="property-MoneyBox">
				<view class="Row" @click="GoUrl(0)">
					<p>总资产(元)</p>
					<span>{{ UserEye ? '0.00' : '*******'}}</span>
				</view>
				<view class="Row" @click="GoUrl(1)">
					<view>总借款(元) <image src="@/static/icon_number_helper_help_cherryblossom.png" mode=""></image> </view>
					<span>{{ UserEye ? '1,000,000.00' : '*******'}}</span>
				</view>
			</view>
			<view class="property-Box" v-for="(item,index) in property" :key="index" 
			:style="{borderRight:index % 2 === 0 ? '1px solid #ddd' : '',borderBottom: item.isTrue ? '' : '1px solid #ddd' }" >
				<p>{{item.text}}</p>
				<span>{{UserEye ? item.subText : '*******'}}</span>
			</view>
		</view>
		<view class="User-RevenueExpenditure">
			<view class="RevenueExpenditure-title">
				<titleVue LFontSize='34'>
					<template #left>
						<view class="TitleEye" @click="SetReEye">
							我的4月收支
							<image v-if="LogonEye" src="../../static/xwr_wealth_my_wallet_eye_close.png" mode=""></image>
							<image v-else src="../../static/xwr_wealth_my_wallet_eye_open.png" mode=""></image>
						</view>
					</template>
					<template #rigth>
						<view class="right">
							<image  src="@/static/user-icon-5.png" mode=""></image> 净值型理财月报
						</view>
					</template>
				</titleVue>
			</view>
			<view class="Logon-money">
				<view class="revenue-and-expenditure">
					<view class="revenue">
						<p>收入(元)</p>
						<span v-if="LogonEye" >****</span>
						<span v-else >0.00</span>
					</view>
					<view class="expenditure">
						<p>支出(元)</p>
						<span v-if="LogonEye">****</span>
						<span v-else >0.00</span>
					</view>
				</view>
				
				<view class="Logon-XT">
					<view class="Money-XT">
						
					</view>
				</view>
				
				<view class="text">
					<p>
						结余(元) 
						<span>{{LogonEye ?  '******' : '0.00'}}</span> 
					</p>
					<span>数据更新截至日为04月10日</span>
				</view>
			</view>
		</view>
		<view class="User-RevenueExpenditure">
			<view class="User-Loan">
				<titleVue width="95%" LFontSize="32" >
					<template #left>
						我的贷款
					</template>
				</titleVue>
				
				<view class="Loan-datali" @click="GoLoan">
					<titleVue width="90%" LFontSize="28" :LFontW="false" Padding="30rpx 0 0 0" >
						<template #left>
							助业房抵贷 (循)
						</template>
					</titleVue>
					<view class="revenue-and-expenditure">
						<view class="revenue">
							<p>贷款金额(元)</p>
							<span >1,000,000.00</span>
						</view>
						<view class="expenditure">
							<p>余额(元)</p>
							<span>1,000,000.00</span>
						</view>
					</view>
				</view>
			</view>
		</view>
		<view class="User-manager">
			<titleVue LFontSize="32" width="90%">
				<template #left>
					专属理财经理
				</template>
			</titleVue>
			<view class="header-text">
				<view class="text-Box">
					<image src="@/static/head-image-1.png" mode=""></image>
					<view class="text">
						<p>卢芳钰 <span>广州分行琶洲支行</span> </p>
						<span>问理财、买理财、就来我的小店</span>
					</view>
				</view>
				<view class="btn">
					立即访问
				</view>
			</view>
		</view>
		<view class="User-outlets">
			<titleVue width="90%" LFontSize="32">
				<template #left>
					我的网点
				</template>
				<template #rigth>
					更多
				</template>
			</titleVue>
			<view class="outlets-image">
				<image src="../../static/outlets-image-1.png" mode=""></image>
			</view>
			<view class="outlets-btn">
				<view class="btn"> <image src="../../static/User-outlets-icon-1.png" mode=""></image> 导航</view>
				<view class="btn"> <image src="../../static/User-outlets-icon-2.png" mode=""></image> 咨询</view>
				<view class="btn"> <image src="../../static/User-outlets-icon-3.png" mode=""></image> 预约</view>
			</view>
		</view>
		<view class="User-prove-safe">
			<view class="prove" v-for="(item,index) in ProveSafe" :key="index">
				<titleVue width="90%" Padding="0 0" LFontSize="32">
					<template #left>
						{{item.name}}
					</template>
					<template #rigth>
						{{item.menu}}
					</template>
				</titleVue>
				<view class="icon-text" v-for="(sum,num) in item.list" :key="num">
					<image :src='`../../static/prove-icon-${index === 0 ? index+1+num :index+2+num+1}.png`' mode=""></image> {{sum}} 
				</view>
			</view>
		</view>
		<view class="User-Image">
			<image src="../../static/User-bj-2.png" mode=""></image>
		</view>
		<view class="User-service">
			<titleVue width="90%" LFontSize="32">
				<template #left>
					我的服务
				</template>
			</titleVue>
			<ListViewVue width="25%" FontSize="25rpx" sizi="50rpx" :listTitle="service"></ListViewVue>
		</view>
		<view class="User-Card">
			<view class="Card-image">
				<view class="image"> <image src="@/static/User-card-icon-5.png" mode=""></image> <span>信用卡</span> </view>
				<p>新客办卡,享诸多权益</p>
			</view>
			<view class="btn">
				立即申请
			</view>
		</view>
	</view>
</template>

<script>
	import occupyVue from '../../components/occupy.vue';
	import ListViewVue from '../../components/ListView.vue';
	import titleVue from '../../components/titleVue.vue';
	export default {
		data() {
			return {
				ListViewList:[
					{name:'我的银行卡',icon:'../../static/user-icon-1.png'},
					{name:'我的消息',icon:'../../static/user-icon-2.png'},
					{name:'我的待办',icon:'../../static/user-icon-3.png'},
					{name:'我的收藏',icon:'../../static/user-icon-4.png'},
				],
				ListViewText:[
					{text:'0',subtitle:'每日签到'},
					{text:'0',subtitle:'我的消息'},
					{text:'更多好礼',subtitle:'我的待办'},
					{text:'0',subtitle:'我的权益'},
				],
				property:[
					{text:'现金',subText:'0.00'},
					{text:'存款',subText:'保本保息乐享安逸基金'},
					{text:'理财',subText:'“闲钱理财” 灵活申赎'},
					{text:'基金',subText:'阳光金选 好基金养老金'},
					{text:'保险',subText:'人有保险无忧',isTrue : true},
					{text:'养老金',subText:'享税收优惠',isTrue : true},
				],
				LogonEye:false,
				UserEye:false,
				RevenueExpenditureEye:false,
				ProveSafe:[
					{name:'我的证明',list:['信用报告','存款证明','电子证明']},
					{name:'安全中心',list:['指纹设置','数字证书','转账限额'],menu:'安全'}
				],
				service:[
					{name:'数字保险',icon:'../../static/User-service-icon-1.png'},
					{name:'意见反馈',icon:'../../static/User-service-icon-2.png'},
					{name:'使用攻略',icon:'../../static/User-service-icon-3.png'},
					{name:'关于app',icon:'../../static/User-service-icon-4.png'},
					{name:'设置',icon:'../../static/User-service-icon-5.png'}
				]
			};
		},
		created() {
			
		},
		onLoad(){
			uni.getStorageSync('account') ?  '' : uni.navigateTo({
				url:'/pages/gesture/gesture'
			})
			console.log(uni.getStorageSync('account') === '');
		},
		components:{
			occupyVue,
			ListViewVue,
			titleVue
		},
		methods:{
			GoUrl(index){
				console.log(index);
				if(index == 1){
					uni.navigateTo({
						url:`/pages/property/property?id=${index}`
					})
					return
				}
				uni.navigateTo({
					url:`/pages/property/property`
				})
			},
			SetEye(){
				this.UserEye = !this.UserEye
			},
			SetReEye(){
				this.LogonEye = !this.LogonEye
			},
			GoLoan(){
				uni.navigateTo({
					url:'/pages/loan/loan?tabs=1'
				})
			},
			Quit(){
				uni.clearStorageSync('account')
				uni.navigateTo({
					url:'/pages/gesture/gesture'
				})
			}
		}
	}
</script>

<style lang="scss" scoped>
	.User{
		width: 100vw;
		background-color: #f4f4f4;
		padding-bottom: 50rpx;
		.User-Title{
			width: 95%;
			margin: 0 auto;
			display: flex;
			flex-wrap: wrap;
			justify-content: space-between;
			align-items: center;
			.User-Quit{
				display: flex;
				align-items: center;
				font-size: 30rpx;
				image{
					width: 40rpx;
					height: 40rpx;
					margin-right: 10rpx;
				}
			}
			.User-Menu{
				display: flex;
				align-items: center;
				image{
					width: 45rpx;
					height: 45rpx;
					margin: 0 20rpx;
				}
				.gif{
					width: 95rpx;
					image{
						width: 80rpx;
						height: 80rpx;
					}
				}
			}
		}
		.User-HeadBox{
			padding: 25rpx;
			display: flex;
			align-items: center;
			justify-content: space-between;
			.Head-Name{
				display: flex;
				align-items: center;	
				image{
					width:  100rpx;
					height: 100rpx;
				}
				.Headt-List{
					margin-left: 20rpx;
					display: flex;
					align-items: center;
					flex-wrap: wrap;
					p{
						width: 100%;
					}
					image{
						width:  130rpx;
						height: 35rpx;
						margin-top: 5rpx;
					}
				}
			}
			image{
				width: 150rpx;
				height: 60rpx;
			}
		}
		.User-ListView{
			margin: 0 auto;
			width: 95%;
			background:url('@/static/User-bj-1.png') ;
			background-size:100% 100% ;
			.ListView{
				display: flex;
				align-items: center;
				padding:10rpx 30rpx;
				font-size: 29rpx;
				.Text{
					padding-top: 20rpx;
					text-align: center;
					width: 33%;
					line-height: 45rpx;
					p{
						font-size: 25rpx;
					}
					span{
						color: #888;
						font-size: 28rpx;
					}
				}
			}
			.ListView-btn{
				padding:20rpx 30rpx;
			}
		}
		.User-notice{
			width: 95%;
			margin: 0 auto;
			display: flex;
			justify-content: space-between;
			align-items: center;
			padding: 20rpx 0;
			background-color: #fff;
			margin-top: 20rpx;
			border-radius: 20rpx;
			.notice-text{
				flex: 1;
				padding:0 20rpx;
				display: flex;
				align-items: center;
				font-size: 28rpx;
				image{
					width: 40rpx;
					height: 40rpx;
				}
				p{
					font-size: 25rpx;
					margin-left: 10rpx;
					color: #555;
				}
			}	
			image{
				padding:0 10rpx;
				width: 40rpx;
				height: 40rpx;
			}
		}
		.User-property{
			width: 95%;
			margin: 0 auto;
			display: flex;
			flex-wrap: wrap;
			align-items: center;
			margin-top: 20rpx;
			background-color: #fff;
			border-radius: 20rpx;
			padding-bottom: 20rpx;
			.property-title{
				width: 90%;
				margin: 0 auto;
				display: flex;
				justify-content: space-between;
				font-size: 30rpx;
				padding: 20rpx;
				.left{
					display: flex;
					align-items: center;
					font-weight: bold;
					font-size: 32rpx;
					image{
						margin-left: 10rpx;
						width: 30rpx;
						height: 30rpx;
					}
				}
				.right{
					display: flex;
					align-items: center;
					image{
						margin: 5rpx 0;
						width: 40rpx;
						height: 40rpx;
					}
					span{
						font-weight: bold;
					}
				}
			}
			.property-MoneyBox{
				width: 95%;
				margin: 0 auto;
				display: flex;
				justify-content: space-between;
				background-color: #f3f3ff;
				border-radius:20rpx;
				padding: 20rpx;
				margin:0 20rpx;
				.Row{
					width: 50%;
					display: flex;
					flex-wrap: wrap;
					align-items: center;
					line-height: 50rpx;
					view{
						width: 100%;
						display: flex;
						align-items: center;
						font-size: 30rpx;
						image{
							width: 40rpx;
							height: 40rpx;
						}
					}
					p{
						font-size: 30rpx;
						width: 100%;
					}
					span{
						font-weight: bold;
						font-size: 35rpx;
					}
				}
			}
			.property-Box{
				width: 40%;
				padding: 10rpx 30rpx;
				line-height: 45rpx;
				p{
					font-size: 24rpx;
					color: #555;
				}
				span{
					font-size: 25rpx;
				}
			}
		}
		.User-RevenueExpenditure{
			width: 95%;
			border-radius: 20rpx;
			margin: 0 auto;
			margin-top: 20rpx;
			background-color: #fff;
			.RevenueExpenditure-title{
				padding:0 35rpx;
				display: flex;
				align-items: center;
				.TitleEye{
					display: flex;
					align-items: center;
					image{
						margin-left: 10rpx;
						width: 35rpx;
						height: 35rpx;
					}
				}
				.right{
					display: flex;
					align-items: center;
					font-size: 25rpx;
					image{
						width: 40rpx;
						height: 40rpx;
						margin-right: 5rpx;
					}
				}
			}
			.Logon-money{
				width: 95%;
				margin: 0 auto;
				padding-bottom: 20rpx;
				.revenue-and-expenditure{
					width: 90%;
					margin: 0 auto;
					display: flex;
					justify-content: space-between;
					align-items: center;
					.revenue{
						line-height: 45rpx;
						p{
							font-size:28rpx;
							color: #888;
							
						}
						span{
							font-size: 35rpx;
						}
					}
					.expenditure{
						text-align: right;
						line-height: 45rpx;
						p{
							color: #888;
							font-size:28rpx;
							
						}
						span{
							font-size: 35rpx;
						}
					}
				}
				.Logon-XT{
					width: 95%;
					height: 8rpx;
					background-color: #ee3a88;
					margin: 0 auto;
					margin-top: 20rpx;
					border-radius: 4rpx;
				}
				.text{
					width: 94%;
					margin: 0 auto;
					margin-top:10rpx;
					font-size: 25rpx;
					color: #888;
					display: flex;
					justify-content: space-between;
					p{
						span{
							color: #000;
							margin-left: 10rpx;
						}
					}
				}
			}
		}
		.User-Loan{
			width: 95%;
			margin: 0 auto;
			padding-bottom: 30rpx;
			.Loan-datali{
				width: 95%;
				margin: 0 auto;
				background-color: #f4f4f4;
				border-radius: 20rpx;
				padding-bottom: 30rpx;
				.revenue-and-expenditure{
					width: 90%;
					margin: 0 auto;
					display: flex;
					justify-content: space-between;
					align-items: center;
					.revenue{
						margin-top: 20rpx;
						line-height: 45rpx;
						p{
							font-size:25rpx;
							color: #888;
							
						}
						span{
							font-size: 30rpx;
							font-weight: bold;
						}
					}
					.expenditure{
						text-align: right;
						line-height: 45rpx;
						p{
							color: #888;
							font-size:25rpx;
							
						}
						span{
							font-size: 30rpx;
							font-weight: bold;
						}
					}
				}
			}
		}
		.User-manager{
			width: 95%;
			margin: 0 auto;
			margin-top: 20rpx;
			background-color: #fff;
			border-radius: 20rpx;
			padding-bottom: 30rpx;
			.header-text{
				width: 95%;
				margin: 0 auto;
				border-radius: 100rpx;
				background-color: #f4f4f4;
				display: flex;
				align-items: center;
				justify-content: space-between;
				.text-Box{
					display: flex;
					align-items: center;
					padding: 10rpx 0;
					image{
						width: 80rpx;
						height: 80rpx;
						padding: 20rpx;
					}
					.text{
						p{
							font-size: 28rpx;
							span{
								font-size: 20rpx;
								margin-left: 10rpx;
								color: #888;
								background:none;
							}
						}
						span{
							background-color: #fff;
							font-size: 20rpx;
						}
					}
				}
				
				.btn{
					padding:10rpx 20rpx;
					border: 1px solid;
					margin: 0 40rpx;
					border-radius: 50rpx;
					font-size: 25rpx;
					color: #7b50af;
				}
			}
			
		}
		.User-outlets{
			width: 95%;
			margin: 0 auto;
			background-color: #fff;
			border-radius: 20rpx;
			margin-top: 20rpx;
			.outlets-image{
				width: 90%;
				margin: 0 auto;
				image{
					width: 100%;
					height: 200rpx;
				}
			}
			.outlets-btn{
				width: 80%;
				padding: 20rpx;
				margin: 0 auto;
				display: flex;
				align-items: center;
				justify-content: space-between;
				.btn{
					display: flex;
					align-items: center;
					font-size:25rpx;
					image{
						width: 35rpx;
						height: 35rpx;
						margin-right: 5rpx;
					}
				}
			}
		}
		.User-prove-safe{
			width: 95%;
			margin: 0 auto;
			margin-top: 20rpx;
			display: flex;
			justify-content: space-between;
			.prove{
				width: 43%;
				background-color: #fff;
				border-radius: 20rpx;
				padding-bottom: 20rpx;
				padding: 20rpx;
				.icon-text{
					display: flex;
					align-items: center;
					margin-top: 40rpx;
					padding:0 20rpx;
					image{
						margin-right: 10rpx;
						width: 40rpx;
						height: 40rpx;
					}
				}
			}
		}
		.User-Image{
			width: 95%;
			margin: 0 auto;
			height: 180rpx;
			margin-top: 20rpx;
			image{
				border-radius: 20rpx;
				width: 100%;
				height: 100%;
			}
		}
		.User-service{
			width: 95%;
			margin: 0 auto;
			margin-top: 20rpx;
			border-radius: 20rpx;
			background-color: #fff;
		}
		.User-Card{
			width: 95%;
			margin: 0 auto;
			background-color: #fff;
			display: flex;
			align-items: center;
			margin-top: 20rpx;
			border-radius: 20rpx;
			justify-content: space-between;
			.Card-image{
				display: flex;
				flex-wrap: wrap;
				align-items: center;
				padding: 20rpx;
				.image{
					width: 100%;
					display: flex;
					align-items: center;
					font-size: 30rpx;
					image{
						width: 60rpx;
						height: 50rpx;
					}
				}
				p{
					width: 100%;
					font-size: 22rpx;
					margin-top: 5rpx;
				}
			}
			.btn{
				padding: 10rpx 15rpx;
				border-radius: 50rpx;
				font-size: 25rpx;
				border: 1px solid ;
				color: #c7876e;
				margin-right: 40rpx;
			}
		}
	}
</style>