<template>
	<view class="LoanRecords">
		<view class="transfer-title">
			<occupyVue hight="90rpx"></occupyVue>
			<backtaberVue  :TitleImage='TitleImage' :rigthIcon="rigthIcon" IconHeight="45rpx" IconWidth="45rpx" Padding="0 30rpx">
				还款计划
			</backtaberVue>
		</view>
		
		<view class="LoanRecords-listView">
			<view class="listView-title">
				<titleVue :icon="true" :LFontW="false" LFontSize="32" RFontSize="30" IconSize="1.5" width="95%" RColor="#9766d2">
					<template #left>
						助业房抵快贷(循)
					</template>
					<template #rigth>
						<text @click="GoUrl(101)">详情</text>
					</template>
				</titleVue>
			</view>
			<view class="listView-Text">
				<view class="Text">
					<span>￥1,000,000.00</span>
					<p>贷款金额</p>
				</view>
				<view class="Text">
					<span>￥1,000,000.00</span>
					<p>贷款金额</p>
				</view>
			</view>
			<view class="CardDali-btn">
				<view class="btn" v-for="(item,index) in cardBtn" :key="index"  :style="{border:index+1 === cardBtn.length ?  'none':'1px soilid #ddd'}" @click="GetIndex(index)">
					{{item}}
				</view>
			</view>
			
			<uni-popup ref="popup" background-color="#f8f8f8" @change="change" :borderRadius='"20px 20px 20px 20px"'>
				<view class="Popup" v-for="(item,index) in Popup" :key="item" :style="{borderRadius: index === 0 ? '40rpx 40rpx 0 0' : '0 0'}" @click="GoUrl(index)">
					{{item}}
				</view>
				<view class="Popup-btn" @click="close">
					取消
				</view>
			</uni-popup>
			
			
			<uni-popup ref="popup" background-color="#f8f8f8" @change="change" :borderRadius='"20px 20px 20px 20px"'>
				<view class="Popup" v-for="(item,index) in Popup" :key="item" :style="{borderRadius: index === 0 ? '40rpx 40rpx 0 0' : '0 0'}" @click="GoUrl(index)">
					{{item}}
				</view>
				<view class="Popup-btn" @click="close">
					取消
				</view>
			</uni-popup>
			
			<uni-popup ref="alertDialog" type="dialog" :borderRadius='"20px 20px 20px 20px"'>
				<uni-popup-dialog  :showClose="false" :type="msgType" confirmText="确定" title="提示" :content="alertDialogText" @confirm="dialogConfirm"></uni-popup-dialog>
			</uni-popup>
		</view>
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
				cardBtn:['还款计划','查看合同','更多'],
				type:'',
				Popup:['还款明细','贷款信息更变','因疫情申请延期还本付息','查询变更协议'],
				msgType:'',
				alertDialogText:'暂不支持查看合同',
				
			};
		},
		components:{
			occupyVue,
			backtaberVue,
			titleVue
		},
		methods:{
			GetIndex(index){
				console.log(index);
				index === 0 ? uni.navigateTo({
					url:'/pages/RepaymentPlan/RepaymentPlan'
				}) : ''
				
				index === 1 ? this.dialogToggle() : ''
				
				if(index === 2){
					this.type = 'bottom'
					// open 方法传入参数 等同在 uni-popup 组件上绑定 type属性
					this.$refs.popup.open('bottom')
				}
			},
			change(e) {
				console.log('当前模式：' + e.type + ',状态：' + e.show);
			},
			close(){
				this.$refs.popup.close()
			},
			GoUrl(index){
				console.log(index);
				index === 0 ? uni.navigateTo({
					url:'/pages/RepaymentDetails/RepaymentDetails'
				}) : ''
				index === 101 ? uni.navigateTo({
					url:'/pages/MyLoan/MyLoan'
				}) : ''
				index === 1 ? uni.navigateTo({
					url:'/pages/InformationChange/InformationChange'
				}) : ''
				if(index === 2 ){
					this.alertDialogText = '不允许申请延期还本付息,如有疑问请联系您的客服经理或质询95595!'
					this.$refs.alertDialog.open()
				}
				if(index === 3 ){
					this.alertDialogText = '您没有变更协议记录'
					this.$refs.alertDialog.open()
				}
				
			},
			dialogToggle(type) {
				this.msgType = type
				this.alertDialogText = '暂不支持查看合同'
				this.$refs.alertDialog.open()
			},
			dialogConfirm() {
				console.log('点击确认')
				this.messageText = `点击确认了 ${this.msgType} 窗口`
				this.$refs.alertDialog.close()
			},
		}
	}
</script>

<style lang="scss">
	.LoanRecords{
		width: 100vw;
		height: 100vh;
		background-color: #f8f8f8;
		.transfer-title{
			background-color: #fff;
		}
		.LoanRecords-listView{
			width: 90%;
			margin: 0 auto;
			background-color: #fff;
			margin-top: 20rpx;
			border-radius: 10rpx;
			.listView-title{
				border-bottom: 1px solid #ebebeb;
			}
			.listView-Text{
				display: flex;
				padding: 30rpx 20rpx;
				border-bottom: 1px solid #ebebeb;
				.Text{
					display: flex;
					flex-wrap: wrap;
					span{
						width: 100%;
						font-size: 40rpx;
						font-weight: bold;
					}
					p{
						color: #999;
						font-size: 25rpx;
						margin-top: 10rpx;
					}
				}
			}
			.CardDali-btn{
				padding: 25rpx 0;
				margin: 0 auto;
				display: flex;
				justify-content: space-between;
				align-items: center;
				.btn{
					flex: 1;
					display: flex;
					align-items: center;
					justify-content: center;
					height: 30rpx;
					border-right: 1px solid #ebebeb;
					color: #7c47be;
					font-size: 28rpx;
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
		.Popup-btn{
			text-align: center;
			padding: 30rpx;
			margin-top: 20rpx;
			color: #7c47be;
			font-size: 32rpx;
			background-color: #fff;
		}
	}
</style>
