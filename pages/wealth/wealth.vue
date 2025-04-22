<template>
	<view class="wealth">
		<HomeTitleVue :WzText="false"></HomeTitleVue>
		<view class="wealth-balance">
			<view class="balance-money">
				<view class="p" @click="ClickEye()">
					总资产(元) 
					<image src="@/static/xwr_wealth_my_wallet_eye_close.png" mode="" v-if="Eye"></image>
					<image src="@/static/xwr_wealth_my_wallet_eye_open.png" mode="" v-else></image> 
				</view>
				<span>{{Eye ? '******' : '0.00' }}</span>
			</view>
			<view class="balance-btn" v-if="token" @click="login">
				登录 
			</view>
		</view>
		<view class="wealth-ViewList">
			<ListViewVue :listTitle="listView" :sizi="'65rpx'" :BgColor="'#fff'" :FontSize="'25rpx'" :Pad="'45rpx 0 '"></ListViewVue>
		</view>
		<view class="wealth-tabs">
			 <z-tabs ref="tabs" :list="tabList" :current="current" :bg-color='TabsBg' active-color='#7a41c6' tab-width="10rpx"  :active-style='{"fontSize":"34rpx","color":"#000"}' :tabs-style="{'width':'550rpx'}"/>
		</view>
		<view class="wealth-fund">
			<view class="fund-Row">
				<p class="title">核心资产</p>
				<span class="subtitle">广发中证A500指数A</span>
				<p class="MaxText">细分行业龙头</p>
				<span class="unumber">022424</span>
				<p class="datali">低门槛，1元起购</p>
				<view class="btn">
					立即购买
				</view>
			</view>
			<view class="fund-Row">
				<p class="title">跟踪红利</p>
				<span class="subtitle">富国中证红利指数增强A</span>
				<p class="MaxText">高分红+低波动</p>
				<span class="unumber">100032</span>
				<p class="datali">低成本，1折申购费</p>
				<view class="btn">
					立即购买
				</view>
			</view>
		</view>
		<view class="wealth-fund-View">
			<view class="Text-View">
				<view class="span">
					<image src="@/static/icon-1.png" mode=""></image>
					 养老金融
				</view>
				<view class="text">
					规划美好生活
					<p>了解详情</p>
				</view>
			</view>
			<view class="Text-View">
				<view class="span">
					<image src="@/static/icon-1.png" mode=""></image>
					 理财夜市
				</view>
				<view class="text">
					好选择 财安心
					<p>了解详情</p>
				</view>
			</view>
		</view>
		<view class="wealth-banner">
			<swiper :indicator-dots="true" :autoplay="true" :interval="3000" :duration="1000">
				<swiper-item v-for="(item,index) in 3" :key="index">
					<image :src="`../../static/wealth-banner-${index+1}.png`" mode=""></image>
				</swiper-item>
			</swiper>
		</view>
		<wealthInvestVue :wealthInvest="wealthInvestOne" :url='urlOne' title="新客金选" SubTitle="新客专属“理”遇，开启财富旅程"></wealthInvestVue>
		<wealthInvestVue :wealthInvest="wealthInvestTow" :url='urlTow' title="安心金选" SubTitle="追求低波，严控回撤，收益更稳定"></wealthInvestVue>
		<view class="wealth-Add">
			
			<view class="invest-title">
				<view class="title">
					投资增益 <image src="@/static/nine_search_right_arrow.png" mode=""></image>
				</view>
				<p>投资股票债券等金融市场产品</p>
			</view>
			
			<view class="wealth-tabs">
				 <z-tabs ref="tabs" :list="tabListAdd" :current="current" :bg-color='TabsBg' active-color='#7a41c6' tab-width="10rpx"  :active-style='{"fontSize":"34rpx","color":"#000"}' :tabs-style="{'width':'550rpx'}"/>
			</view>
			
			<view class="wealth-Add-ListView">
				<view class="ListView-image">
					<image src="@/static/wealth-bj-4.png" mode=""></image>
				</view>
				<view class="ListView-Text">
					<p>攻守有道，胜券“债”握</p>
					<view class="listView-Row">
						<view class="Row-Title">
							3.74<span>%</span>
						</view>
						<view class="Row-Text">
							中加纯债债券
						</view>
					</view>
					<view class="listView-Row">
						<view class="Row-Text">
							近一年收益率
						</view>
						<view class="Row-Btn">
							阳光精选
						</view>
					</view>
				</view>
			</view>
			
			<view class="wealth-Add-ListView">
				<view class="ListView-image">
					<image src="@/static/wealth-bj-5.png" mode=""></image>
				</view>
				<view class="ListView-Text">
					<p>历史每半年均正收益</p>
					<view class="listView-Row">
						<view class="Row-Title">
							3.81<span>%</span>
						</view>
						<view class="Row-Text">
							长城短债A
						</view>
					</view>
					<view class="listView-Row">
						<view class="Row-Text">
							近一年收益率
						</view>
						<view class="Row-Btn">
							阳光精选
						</view>
					</view>
				</view>
				
			</view>
		</view>
		<view class="wealth-points">
			<titleVue LFontSize="35">
				<template #left>
					股市大赢家 天天赚积分
				</template>
			</titleVue>
			<view class="Points-Row">
				<view class="Row">
					<view class="Row-ListView">
						<image src="@/static/Home-listIcon-3.png" mode=""></image> 猜涨跌
					</view>
					<view class="Row-ListView">
						<image src="@/static/Home-listIcon-4.png" mode=""></image> 幸运砸金蛋
					</view>
					<view class="Row-ListView">
						<image src="@/static/Home-listIcon-5.png" mode=""></image> 每日签到
					</view>
				</view>
				
				<view class="Row">
					<view class="Row-ListView">
						<image src="@/static/Home-listIcon-6.png" mode=""></image> K线训练营
					</view>
					<view class="Row-ListView">
						<image src="@/static/Home-listIcon-7.png" mode=""></image> 答题赢积分
					</view>
					<view class="Row-ListView">
						<image src="@/static/Home-listIcon-8.png" mode=""></image> 证券开户
					</view>
				</view>
			</view>
		</view>
		<view class="wealth-Zone">
			<titleVue LFontSize="35" :icon="true" RColor="#aaaaaa">
				<template #left>
					财富资讯
				</template>
				<template #rigth>
					更多
				</template>
			</titleVue>
			<view class="Zone-ListView">
				<view style="flex: 1;">
					<view class="ListView-Text">
						各方协同发力 积极推动银发经济发展
					</view>
					<view class="ListView-SubTitle">
						<text>光明网</text>
						<text>2-13</text>
					</view>
				</view>
			</view>
			<view class="Zone-ListView">
				<view style="flex: 1;">
					<view class="ListView-Text">
						国家级认可!卡奥斯大模型入选工业领域数据要素应用场景...
					</view>
					<view class="ListView-SubTitle">
						<text>大众新闻-大..</text>
						<text>2-10</text>
					</view>
				</view>
				<image src="@/static/highlights-bj-3.png" mode=""></image>
			</view>
		</view>
	</view>
</template>

<script>
	import HomeTitleVue from '../../components/HomeTitle.vue';
	import ListViewVue from '../../components/ListView.vue';
	import wealthInvestVue from '../../components/wealth-invest.vue';
	import titleVue from '../../components/titleVue.vue';
	export default {
		data() {
			return {
				listView:[
					{
						name:'存款',
						icon:'../../static/Home-listIcon-1.png'
					},
					{
						name:'缴费',
						icon:'../../static/Home-listIcon-2.png'
					},
					{
						name:'资产',
						icon:'../../static/Home-listIcon-3.png'
					},
					{
						name:'信用卡',
						icon:'../../static/Home-listIcon-4.png'
					},
					{
						name:'贷款',
						icon:'../../static/Home-listIcon-5.png'
					},
					{
						name:'贷款',
						icon:'../../static/Home-listIcon-6.png'
					},
					{
						name:'基金',
						icon:'../../static/Home-listIcon-7.png'
					},
					{
						name:'个人养老金',
						icon:'../../static/Home-listIcon-8.png'
					},
					{
						name:'权益服务',
						icon:'../../static/Home-listIcon-9.png'
					},
					{
						name:'全部',
						icon:'../../static/Home-listIcon-10.png'
					}
				],
				current: 0,
				tabList: ['精选基金','精选理财','精选存款'],
				tabListAdd: ['业绩领先','鼎流名人','热门行业'],
				TabsBg:'none',
				wealthInvestOne:[
					{
						name:"阳光金新客天天购(100天最低持有)|代销光大理财",
						percentage:'3.17%',
						percentageSuhTitle:'成立以来年化',
						datali:'持有100天后每日可赎',
						subDatali:['1.00元起购','较低风险'],
						prompt:'业绩比较基准:2.7%-3.2%',
						SubTitlePrompt:'业绩比较基准是管理人基于产品性质、投资策…'
					},
					{
						name:"鸿运灵活最短持有7天7号代销中邮理财",
						percentage:'3.55%',
						percentageSuhTitle:'成立以来年化',
						datali:'最低持有7天可赎回',
						subDatali:['1.00元起购','较低风险'],
						prompt:'业绩比较基准:1.9%至3.3%',
						SubTitlePrompt:'业绩比较基准由产品管理人依据理财产品的投…'
					},
					{
						name:"周周鑫57号A|代销浦银理财",
						percentage:'2.98%',
						percentageSuhTitle:'成立以来年化',
						datali:'最低持有7天可赎回',
						subDatali:['1.00元起购','较低风险'],
						prompt:'业绩比较基准:2.22%',
						SubTitlePrompt:'业绩比较基准由产品管理人依据产品的投资范…'
					}
				],
				wealthInvestTow:[
					{
						name:"阳光金增利稳健天天购定制(30天最... | 代销光大理财",
						percentage:'3.70%',
						percentageSuhTitle:'成立以来年化',
						datali:'持有30天后每日可赎',
						subDatali:['1.00元起购','较低风险'],
						prompt:'业绩比较基准:2.15%-2.75%',
						SubTitlePrompt:'本产品主要投资于债券等，适度投资于优先股…'
					},
					{
						name:"阳光金增利稳健乐享天天购5号(7天… | 代销光大理财",
						percentage:'3.72%',
						percentageSuhTitle:'成立以来年化',
						datali:'最低持有7天可赎回',
						subDatali:['1.00元起购','较低风险'],
						prompt:'业绩比较基准:2.10%-2.60%',
						SubTitlePrompt:'本产品主要投资于债券等，适度投资于优先股…'
					},
					{
						name:"灵活·鸿运最短持有14天7号 | 代销中邮理财e",
						percentage:'3.70%',
						percentageSuhTitle:'成立以来年化',
						datali:'最低持有14天可赎回',
						subDatali:['1.00元起购','较低风险'],
						prompt:'业绩比较基准:2.0%至3.4%',
						SubTitlePrompt:'业绩比较基准由产品管理人依据理财产品的投…'
					}
				],
				urlOne:'../../static/bg_function_customize_credit_card_small.png',
				urlTow:'../../static/ic_custonize_my_money_small_bg.png',
				Eye:true,
				token:''
			};
		},
		components:{
			HomeTitleVue,
			ListViewVue,
			wealthInvestVue,
			titleVue
		},
		methods:{
			ClickEye(){
				this.Eye = !this.Eye
			},
			login(){
				uni.navigateTo({
					url:'/pages/gesture/gesture'
				})
			}
		},
		onShow() {
			console.log(this.$token === "");
			this.$token ? this.token = false :this.token = true
		}
	}
</script>

<style lang="scss" scoped>
	.wealth{
		width: 100vw;
		background: url('@/static/bg_wealth_top_eleven.png')no-repeat;
		background-size:100%;
		background-color: #f7f7f7;
		padding-bottom: 50rpx;
		.wealth-balance{
			width: 90%;
			margin: 0 auto;
			margin-top: 20rpx;
			background: url('@/static/wealth-bg.png');
			background-size:100% 100% ;
			display: flex;
			justify-content: space-between;
			align-items: center;
			.balance-money{
				padding: 40rpx;
				line-height: 50rpx;
				.p{
					display: flex; 
					align-items: center;
					font-size: 35rpx;
					image{
						margin-left: 15rpx;
						width: 35rpx;
						height: 35rpx;
					}
				}
				span{
					font-size: 35rpx
				}
			}
			.balance-btn{
				margin:0 40rpx;
				border: 1px solid;
				font-size: 25rpx;
				color: #c0866f;
				padding:10rpx 40rpx;
				border-radius: 50rpx;
			}
		}
		.wealth-ViewList{
			width:90%;
			margin: 0 auto;
			margin-top: 20rpx;
		}
		.wealth-tabs{
			width: 90%;
			margin: 0 auto;
			margin-top: 20rpx;
		}
		.wealth-fund{
			width: 90%;
			margin: 0 auto;
			display: flex;
			align-items: center;
			padding: 10rpx 0;
			border-radius: 20rpx;
			margin-top: 10rpx;
			background: linear-gradient(to bottom,#fef6eb,#fff);
			.fund-Row{
				width: 50%;
				padding: 30rpx;
				line-height: 48rpx;
				.title{
					font-size: 35rpx;
					font-weight: bold;
				}
				.subtitle{
					font-size: 25rpx;
					color: #555;
				}
				.MaxText{
					font-size: 40rpx;
					font-weight: bold;
					color: #d35f36;
				}
				.unumber{
					font-size: 25rpx;
					color: #888;
				}
				.datali{
					font-size: 28rpx;
					color: #666;
				}
				.btn{
					width: 100rpx;
					height: 100%;
					text-align: center;
					font-size: 23rpx;
					color: #fff;
					padding: 0 20rpx;
					border-radius: 50rpx;
					background-color: #d35f36;
					margin-top: 50rpx;
				}
			}
		}
		.wealth-fund-View{
			width: 90%;
			margin: 0 auto;
			display: flex;
			justify-content: space-between;
			.Text-View{
				width: 49%;
				margin-top: 20rpx;
				height: 48%;
				background-color: #fff;
				border-radius: 20rpx;
				padding: 20rpx 0;
				line-height: 45rpx;
				.span{
					width: 90%;
					margin: 0 auto;
					display: flex;
					font-size: 28rpx;
					font-weight: bold;
					align-items: center;
					image{
						width: 50rpx;
						height: 50rpx;
					}
				}
				.text{
					width: 85%;
					margin: 0 auto;
					font-size: 28rpx;
					p{
						color: #b1927b;
						font-size: 22rpx;
					}
				}
			}
		}
		.wealth-banner{
			width: 90%;
			margin: 0 auto;
			margin-top: 30rpx;
			height: 170rpx;
			swiper{
				width: 100%;
				height: 100%;
				/deep/.uni-swiper-dot{
					width: 5rpx;
					height: 5rpx;
					border-radius: 10rpx;
				}
				/deep/.uni-swiper-dot-active{
					width: 20rpx;
					height: 5rpx;
					border-radius: 10rpx;
					background-color: #753cba;
				}
				swiper-item{
					image{
						width: 100%;
						height: 170rpx;
					}
				}
				
			}
		}
		.wealth-Add{
			width: 90%;
			padding-bottom: 50rpx;
			margin: 0 auto;
			margin-top: 20rpx;
			background:url('@/static/bg_wealth_bg.png')no-repeat;
			background-size: 100% 100%;
			.invest-title{
				height: 100rpx;
				padding: 10rpx 20rpx;
				line-height: 45rpx;
				.title{
					margin-top: 40rpx;
					display: flex;
					align-items: center;
					font-size: 35rpx;
					image{
						width: 30rpx;
						height: 30rpx;
					}
				}
				p{
					width: 100%;
					font-size: 25rpx;
					color: #888;
				}
			}
			.wealth-tabs{
				width: 90%;
				margin: 0 auto;
				margin-top: 50rpx;
			}
			.wealth-Add-ListView{
				margin: 0 auto;
				margin-top: 30rpx;
				width: 90%;
				display: flex;
				.ListView-image{
					image{
						width: 150rpx;
						height: 130rpx;
					}
				}
				.ListView-Text{
					flex: 1;
					margin-left:20rpx;
					.listView-Row{
						display: flex;
						align-items: center;
						color: #bc683a;
						.Row-Title{
							font-size: 40rpx;
							margin-right: 50rpx;
							span{
								font-size: 28rpx;
							}
						}
						.Row-Text{
							font-size: 28rpx;
							color: #666;
							margin: 10rpx 0;
						}
						.Row-Btn{
							border: 1px solid;
							margin-left: 20rpx;
							font-size: 20rpx;
							padding:5rpx 10rpx;
							border-radius: 10rpx;
							background-color: #ffeee3;
						}
					}
				}
			}
		}
		.wealth-points{
			width: 90%;
			margin: 0 auto;
			.Points-Row{
				width: 100%;
				display: flex;
				align-items: center;
				justify-content: space-between;
				.Row{
					width: 48%;
					border-radius:20rpx;
					background-color: #fff;
					.Row-ListView{
						display: flex;
						align-items: center;
						image{
							width: 45rpx;
							height: 45rpx;
							margin-right: 10rpx;
						}
						padding: 20rpx;
						font-size: 28rpx
					}
				}
				
			}
		}
		.wealth-Zone{
			width: 90%;
			margin: 0 auto;
			.Zone-ListView{
				padding: 30rpx;
				background-color: #fff;
				border-radius: 20rpx;
				display: flex;
				margin-top: 20rpx;
				.ListView-Text{
					width: 100%;
					height: 100rpx;
					font-size: 25rpx;
				}
				.ListView-SubTitle{
					width: 100%;
					font-size: 20rpx;
					display: flex;
					align-content: center;
					justify-content: space-between;
				}
				image{
					width: 200rpx;
					height: 140rpx;
					margin-left: 50rpx;
				}
			}
		}
	}
	
</style>
