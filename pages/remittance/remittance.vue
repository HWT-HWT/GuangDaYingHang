<template>
	<view class="remittance">
		<view class="transfer-title">
			<occupyVue hight="90rpx"></occupyVue>
			<backtaberVue  :TitleImage='TitleImage' :rigthIcon="rigthIcon" IconHeight="45rpx" IconWidth="45rpx" Padding="0 30rpx">
				转账汇款
			</backtaberVue>
		</view>
		<view class="remittance-box">
			<view class="remittance-list" v-for="(item,index) in transferBodyListOne" :key="index">
				<transferBodyVue :placeholder='item.placeholder' :icon="item.imageIcon" :iconSize="item.iconSize"  v-model='item.value' :input='index === 2 ? true : false ' :array='index === 3 ?  transferBodyList[index].array : "" '>
					<template #text>
						{{item.name}} 
					</template>
				</transferBodyVue>
			</view>
		</view>
		
		<view class="remittance-box">
			<view class="remittance-list" v-for="(item,index) in transferBodyListTow" :key="index">
				<transferBodyVue :placeholder='item.placeholder' :icon="item.imageIcon"   v-model='item.value' :input='index === 2 ? true : false ' :array='index === 3 ?  transferBodyList[index].array : "" '>
					<template #text>
						{{item.name}}
					</template>
				</transferBodyVue>
			</view>
		</view>
		
		<view class="CommonPayee-money">
			<view class="title">
				<text class="text">转账金额</text>
				<text style="color: dodgerblue;">限额查询</text>
			</view>
			<view class="CommonPayee-list-box">
				<view class="list-content" style="border-bottom:1rpx solid #ddd;">
					<view class="image">
						￥
					</view>
					<view class="text">
						<input type="text" placeholder="免手续费" placeholder-style="color:#ccc;font-size:35rpx; font-weight:normal;">
					</view>
				</view>
				<view class="list-content">
					<text style="color: #ccc;"></text>
				</view>
			</view>
		</view>
		
		<view class="remittance-listView">
			<span>转账用途</span>
			<view class="icon">
				<text>非必填</text>
				<image src="@/static/upsdk_card_arrow_right.webp" mode=""></image>
			</view>
		</view>
		
		<view class="remittance-tisi">
			<span>实时 <text>(实时发出)</text> </span>
			
			<p>更换转账方式</p>
		</view>
		
		<view class="Account-Add">
			<view class="btn">
				下一步
			</view>
		</view>
		
		<view class="OtherCards-tisi">
			<p>温馨提示:</p>
			<span>1.为了您的资金安全，请勿轻信任何以公检法、网购刷单、客服退款、贷款代办、信用卡提额、高收益理财等为由进行转账要求，谨防电信网络诈骗。</span> <br>
			<span>2.不扫描可疑二维码，不下载可疑APP，请妥善保管卡号、密码、短信验证码等个人重要信息。</span>
		</view>
	</view>
</template>

<script>
	import transferBodyVue from '@/components/transfer-Body.vue'
	import occupyVue from '../../components/occupy.vue'
	import backtaberVue from '../../components/backtaber.vue'
	import titleVue from '../../components/titleVue.vue'
	export default {
		data() {
			return {
				TitleImage:'../../static/ic_black_left_back.png',
				rigthIcon:[{icon:'../../static/info_details_icon_click_more.png'}],
				transferBodyListOne:[
					{
						placeholder:'请输入收款户名/首字母检索',name:'收款户名',imageIcon:'../../static/remittance-icon-1.png', value:'', iconSize:'2'
					},
					{
						placeholder:'请输入收款账号/手机号',name:'收款账户',imageIcon:'../../static/remittance-icon-2.png', value:'', iconSize:'2'
					},
					{
						placeholder:'请选择收款银行',name:'收款银行', value:'',imageIcon:'../../static/arraw_right.webp'
					},
				],
				
				transferBodyListTow:[
					{
						name:'付款账户',imageIcon:'../../static/arraw_right.webp', value:'622663******0436'
					},
					{
						name:'可用余额', value:'0.00'
					},
				],
			};
		},
		components:{
			transferBodyVue,
			occupyVue,
			backtaberVue,
			titleVue
		}
		
	}
</script>

<style lang="scss" scoped>
	.remittance{
		width: 100vw;
		background-color: #f2f2f2;
		.transfer-title{
			background-color: #fff;
		}
		.remittance-box{
			background-color: #fff;
			margin-top: 20rpx;
		}
		.CommonPayee-money{
			width: 100%;
			margin: 0 auto;
			margin-top:20rpx;
			background-color: #fff;
			.title{
				width: 90%;
				margin: 0 auto;
				display: flex;
				justify-content: space-between;
				align-items: center;
				font-size: 32rpx;
				background-color: #fff;
				padding-top: 30rpx;
				.text{
					font-weight: bold;
					font-size: 35rpx
				}
			}
			.CommonPayee-list-box{
				width: 100%;
				margin: 0 auto;
				background-color: #fff;
				.list-content{
					width: 90%;
					margin: 0 auto;
					display: flex;
					align-items: center;
					margin-top: 30rpx;
					padding-bottom: 20rpx;
					font-size: 30rpx;
					.image{
						display: flex;
						align-items: center;
						font-size: 50rpx;
						font-weight: bold;
					}
					.text{
						flex: 1;
						margin-left: 20rpx;
						input{
							font-size: 50rpx;
							font-weight: bold;
						}
					}
				}
			}
		}
		.remittance-listView{
			margin-top: 20rpx;
			font-size: 32rpx;
			display: flex;
			justify-content: space-between;
			padding: 30rpx;
			background-color: #fff;
			.icon{
				display: flex;
				align-items: center;
				color: #888;
				image{
					width: 40rpx;
					height: 40rpx;
					padding:0 10rpx;
				}
			}
		}
		.remittance-tisi{
			display: flex;
			justify-content: space-between;
			padding: 30rpx;
			font-size: 32rpx;
			span{
				color:#f48f18;
				text{
					color:#888;
					margin: 0 15rpx;
				}
			}
			p{
				color: #8e62bf;
			}
		}
		.Account-Add{
			width: 95%;
			margin: 0 auto;
			display: flex;
			justify-content: space-between;
			.btn{
				width: 100%;
				padding: 35rpx 0;
				border-radius: 10rpx;
				background-color: #ba98e5;
				color: #fff;
				margin-top: 20rpx;
				display: flex;
				justify-content: center;
			}
		}
		.OtherCards-tisi{
			width: 90%;
			margin: 0 auto;
			margin-top: 50rpx;
			p{
				color: #fd8d0a;
				font-weight: bold;
			}
			span{
				font-size: 25rpx;
				color: #888;
			}
		}
	}
</style>
