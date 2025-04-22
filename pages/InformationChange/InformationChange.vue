<template>
	<view class="InformationChange">
		<view class="transfer-title">
			<occupyVue hight="90rpx"></occupyVue>
			<backtaberVue  :TitleImage='TitleImage' :rigthIcon="rigthIcon" IconHeight="45rpx" IconWidth="45rpx" Padding="0 30rpx">
				贷款信息变更
			</backtaberVue>
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
		
		<view class="remittance">
			<view class="remittance-list" v-for="(item,index) in transferBodyList" :key="index">
				<transferBodyVue :placeholder='item.placeholder' :icon="item.imageIcon"   v-model='item.value' :input='index === 2 ? true : false ' :array='index === 3 ?  transferBodyList[index].array : "" '>
					<template #text>
						{{item.name}}
					</template>
				</transferBodyVue>
			</view>
		</view>
	</view>
</template>

<script>
	import occupyVue from '../../components/occupy.vue'
	import backtaberVue from '../../components/backtaber.vue'
	import transferBodyVue from '../../components/transfer-Body.vue';
	export default {
		data() {
			return {
				TitleImage:'../../static/ic_black_left_back.png',
				rigthIcon:[{icon:'../../static/info_details_icon_click_more.png'}],
				cardBtn:['还款计划','查看合同','更多'],
				transferBodyList:[
					{
						name:'变更类型', value:'请选择',imageIcon:'../../static/arraw_right.webp'
					},
				],
				transferBodyListTow:[
					{
						name:'产品名称', value:'助业房抵快贷 (循)'
					},
					{
						name:'借据号', value:'388824770001RH001'
					},
				],
			};
		},
		components:{
			occupyVue,
			backtaberVue,
			transferBodyVue
		}
	}
</script>

<style lang="scss">
	.InformationChange{
		width: 100vw;
		min-height: 100vh;
		background-color: #f8f8f8;
		.transfer-title{
			background-color: #fff;
			position: fixed;
			top: 0;
			z-index: 999;
		}
		.remittance-box{
			background-color: #fff;
			margin-top: 170rpx;
		}
		.remittance{
			margin-top: 20rpx;
			background-color: #fff;
		}
	}
</style>
