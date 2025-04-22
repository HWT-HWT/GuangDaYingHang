<template>
	<view class="loan-TopTitle" >
		<view :style="{opacity:Scollor>1 ? '0':'1'}">
			<occupyVue hight="90rpx"></occupyVue>
			<backtaberVue :TitleImage='TitleImage' :rigthIcon='rigthIcon' :RightMax='1' :isText='false'>
				<text :style="{color: Color}">{{name}}</text>
			</backtaberVue>
		</view>
		<view class="hide" :style="{opacity:Scollor/50}" >
			<occupyVue hight="90rpx"></occupyVue>
			<backtaberVue :TitleImage='TitleImage' :rigthIcon='rigthIcon' :RightMax='1' :isText='false'>
				{{name}}
			</backtaberVue>
		</view>
	</view>
</template>

<script>
	import occupyVue from './occupy.vue';
	import backtaberVue from './backtaber.vue';
	export default {
		name:"loan-Title",
		data() {
			return {
				
			};
		},
		props:{
			TitleImage:{
				type:String
			},
			rigthIcon:{
				type:Array
			},
			name:{
				type:String
			},
			Scollor:{
				type:Number,
				default:0
			},
			Color:{
				type:String,
				default:'#000'
			}
		},
		components:{
			occupyVue,
			backtaberVue
		},
	}
</script>

<style lang="scss">
	.hide{
		width: 100%;
		background-color: #fff;
		position: fixed;
		top: 0;
		z-index: 999;
	}
</style>