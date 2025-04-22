<template>
	<view class="loan">
		<view class="loan-image-1">
			<image src="@/static/loan-bg-1.png" mode=""></image>
		</view>
		<view class="loan-person">
			<view class="person">
				<titleVue LFontSize="25" :LFontW="false" Padding="20rpx">
					<template #left>
						个人贷款
					</template>
				</titleVue>
				<view class="person-box">
					<view class="Title">
						<span> 30 <text>万</text> </span>
						<p>最高额度(万)</p>
					</view>
					<view class="SubTitle">
						<p>最长可贷期限36个月</p>
						<span>年利率(单利)低至<text style="color: #000; font-weight: bold;">5.6%</text>起(以实际审批为准),保费费率详询保险公司</span>
					</view>
				</view>
			</view>
			<view class="person">
				<titleVue LFontSize="25" :LFontW="false" Padding="20rpx">
					<template #left>
						住房贷款
					</template>
				</titleVue>
				<view class="person-box">
					<view class="Title">
						<span> 8.5成 <text>(房屋价值)</text> </span>
						<p>最高额度(万)</p>
					</view>
					<view class="SubTitle">
						<p>最长可贷期限30年</p>
						<span>利率以当地政策及实际审批为准</span>
					</view>
				</view>
			</view>
			<view class="person-btn">
				查看全部 <image src="@/static/purple_right-1.png" mode=""></image>
			</view>
		</view>
		<view class="loan-other">
			<titleVue LFontSize="35" :icon="true" IconSize="1.5" Padding="15rpx">
				<template #left>
					其他贷款
				</template>
				
				<template #rigth>
					更多
				</template>
			</titleVue>
			
			<image src="@/static/loan-image-2.png" mode=""></image>
		</view>
		<view class="loan-minute">
			<titleVue Padding="20rpx" LFontSize="35">
				<template #left>
					小微贷款
				</template>
			</titleVue>
			
			<image src="@/static/loan-bg-2.png" mode=""></image>
			<image src="@/static/loan-bg-3.png" mode=""></image>
		</view>
	
		<view class="loan-service">
			<titleVue LFontSize="35" Padding="30rpx">
				<template #left>
					贷款服务
				</template>
			</titleVue>
			<ListView :listTitle="loanService" width="25%" Pad="20rpx 0" FontSize="25rpx" BgColor="#fff"></ListView>
		</view>
		<view class="loan-inquiry">
			<titleVue Padding="30rpx" LFontSize="35">
				<template #left>
					贷款资讯
				</template>
				<template #rigth>
					更多
				</template>
			</titleVue>
			
			<view class="inquiry-listView">
				<view class="listView">
					<view class="listView-Text">
						<p>事关就业!人社部:今年总体稳定并呈向好态势</p>
						<view class="Text">
							<text>第一财经Yiwealth</text>
							<text>03/10 16:21</text>
						</view>
					</view>
					<view class="listView-image">
						<image src="@/static/loan-inquiry-1.png" mode=""></image>
					</view>
				</view>
			</view>
			
			<view class="inquiry-listView">
				<view class="listView">
					<view class="listView-Text">
						<p>LPR维持不变 对经济和消费释放出哪些信号</p>
						<view class="Text">
							<text>新黄河</text>
							<text>02/21 10:25</text>
						</view>
					</view>
					<view class="listView-image">
						<image src="@/static/loan-inquiry-2.png" mode=""></image>
					</view>
				</view>
			</view>
			
			<view class="inquiry-listView">
				<view class="listView">
					<view class="listView-Text">
						<p>二套房最低首付比例降至两成!这地官宣公积金新政</p>
						<view class="Text">
							<text>第一财经Yiwealth</text>
							<text>01/06 13:31</text>
						</view>
					</view>
					<view class="listView-image">
						<image src="@/static/loan-inquiry-3.png" mode=""></image>
					</view>
				</view>
			</view>
		</view>
		
	</view>
</template>

<script>
	import occupyVue from '@/components/occupy.vue'
	import backtaberVue from '@/components/backtaber.vue'
	import titleVue from '@/components/titleVue.vue';
	import ListView from '@/components/ListView.vue'
	export default {
		data() {
			return {
				TitleImage:'@/static/ic_black_left_back.png',
				rigthIcon:[{icon:'@/static/info_details_icon_click_more.png'}],
				tabs:true,
				loanService:[
					{name:'贷款计算器',icon:'../../static/loan-service-1.png'},
					{name:'个人信用报告',icon:'../../static/loan-service-2.png'},
					{name:'小微贷款授权',icon:'../../static/loan-service-3.png'},
					{name:'配偶授权',icon:'../../static/loan-service-4.png'},
					{name:'无还本续贷',icon:'../../static/loan-service-5.png'}
				]
			};
		},
		components:{
			occupyVue,
			backtaberVue,
			titleVue,
			ListView
		},
		methods:{
			NextTab(index){
				console.log(index === 1);
				index === 1 ? this.tabs = false : this.tabs = true
			}
		}
	}
</script>

<style lang="scss" scoped>
	.loan{
		margin-top: 160rpx;
		background-color: #f8f8f8;
		.transfer-title{
			background-color: #fff;
		}
		.loan-image-1{
			width: 90%;
			height: 380rpx;
			margin: 0 auto;
			margin-top: 20rpx;
			image{
				width: 100%;
				height: 100%;
				margin: 0 auto;
			}
		}
		.loan-person{
			width: 90%;
			margin: 0 auto;
			background-color: #fff;
			border-radius: 20rpx;
			margin-top: 20rpx;
			.person-box{
				padding:0 20rpx;
				display: flex;
				justify-content: space-between;
				padding-bottom: 20rpx;
				border-bottom:1px solid #ddd;
				.Title{
					
					width: 40%;
					line-height: 45rpx;
					span{
						color: #c27b60;
						font-size: 40rpx;
						text{
							font-size: 22rpx;
						}
					}
					p{
						font-size: 25rpx;
						color: #999;
					}
				}
				.SubTitle{
					flex: 1;
					p{
						font-size: 30rpx;
					}
					span{
						
						font-size: 24rpx;
						color: #999;
					}
					
				}
			}
			.person-btn{
				padding: 20rpx;
				font-size: 25rpx;
				display: flex;
				align-items: center;
				justify-content: center;
				image{
					width: 25rpx;
					height: 25rpx;
					margin-left: 5rpx;
				}
			}
		}
		.loan-other{
			width: 90%;
			margin: 0 auto;
			margin-top: 20rpx;
			image{
				width: 100%;
				height: 180rpx;
				margin-top: 10rpx;
			}
		}
		.loan-minute{
			width: 90%;
			margin: 0 auto;
			image{
				width: 100%;
				height: 250rpx;
				margin-top: 10rpx;
			}
		}
		.loan-service{
			width: 90%;
			margin: 0 auto;

			margin-top: 20rpx;
			border-radius: 20rpx;
		}
		.loan-inquiry{
			width: 90%;
			margin: 0 auto;
			.inquiry-listView{
				background-color: #fff;
				border-radius: 20rpx;
				margin-bottom: 20rpx;
				.listView{
					display: flex;
					justify-content: space-between;
					padding: 30rpx;
					.listView-Text{
						display: flex;
						flex-wrap: wrap;
						font-size: 30rpx;
						.Text{
							width: 100%;
							margin-top: 20rpx;
							font-size: 22rpx;
							color: #999;
							display: flex;
							justify-content: space-between;
						}
					}
					.listView-image{
						flex: 1;
						margin-left: 20rpx;
						image{
							width: 250rpx;
							height: 150rpx;
						}
					}
				}
				
			}
		}
	}
</style>
