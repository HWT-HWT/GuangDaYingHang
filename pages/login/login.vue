<template>
	<view class="login">
		<occupyVue hight="90rpx"></occupyVue>
		<view class="login-title">
			<image src="@/static/dialog_profession_black_arrow.png" mode="" @click="black"></image>
			<image src="@/static/shortcut_menu_kefu.png" mode=""></image>
		</view>
		<view class="login-MaxLog">
			<image src="@/static/ebank_logo.webp" mode=""></image>
		</view>
		<view class="login-input">
			<view class="input-name">
				签约手机 :
			</view>
			<view class="input-Box">
				<input  type="number" placeholder="请输入签约手机号" maxlength="11" />
			</view>
		</view>
		<view class="login-input">
			<view class="input-name">
				验证码 :
			</view>
			<view class="input-Box">
				<input type="text" placeholder="请输入验证码"  />
			</view>
			<view class="input-btn">
				获取验证码
			</view>
		</view>
		<view class="login-checkbox">
			<label>
				<checkbox @click="checkboxBtn()" iconColor="#fff" activeBackgroundColor='#7d64ce' borderColor='#ddd' activeBorderColor='#ddd'  :checked="Ischeckbox"/>
			</label>
			<text>我已阅读并同意<text>《中国光大银行手机银行客户服务协议》《中国光大银行手机银行个人信息保护政策》</text></text>
		</view>
		<view class="login-Btn">
			登录
		</view>
		<view class="login-SubName">
			<text>快速注册</text>
			<text>忘记密码</text>
		</view>
		<view class="login-logo">
			<view class="logo-box">
				<image src="@/static/logo_wechat.webp" mode=""></image>
				<p>微信登录</p>
			</view>
		</view>
		
	</view>
</template>

<script>
	import occupyVue from '../../components/occupy.vue'
	export default {
		data() {
			return {
				Ischeckbox:false
			}
		},
		methods: {
			checkboxBtn(){
				this.Ischeckbox = !this.Ischeckbox
			},
			black(){
				uni.navigateBack()
			}
		},
		components:{
			occupyVue
		}
		
	}
</script>

<style scoped lang="scss">
	.login{
		width: 100vw;
		height: 100vh;
		.login-title{
			width: 90%;
			margin: 0 auto;
			display: flex;
			align-items: center;
			justify-content: space-between;
			image{
				width: 50rpx;
				height: 50rpx;
			}
		}
		.login-MaxLog{
			display: flex;
			align-items: center;
			justify-content: center;
			margin:100rpx auto;
			image{
				width: 500rpx;
				height: 100rpx;
			}
		}
		.login-input{
			width: 80%;
			margin: 0 auto;
			display: flex;
			align-items: center;
			border-bottom: 1px solid #e8e8e8;
			padding: 25rpx;
			margin-top: 20rpx;
			.input-name{
				font-size: 34rpx;
			}
			.input-Box{
				margin-left: 20rpx;
				flex: 1;
				input{
					font-size: 34rpx;
				}
			}
			.input-btn{
				border: 1px solid;
				padding: 15rpx;
				border-radius: 10rpx;
				font-size: 28rpx;
				color: #7d64ce;
			}
		}
		.login-checkbox{
			width: 90%;
			margin: 0 auto;
			margin-top: 40rpx;
			font-size: 28rpx;
			display: flex;
			flex-wrap: nowrap;
			justify-content: center;
			checkbox{
				transform: scale(0.6);
				
			}
			text{
				width: 100%;
				line-height: 45rpx;
				margin-left: 10rpx;
				text{
					color: #2d84ec;
					
				}
			}
		}
		.login-Btn{
			width: 80%;
			border: 1px solid;
			padding:20rpx;
			display: flex;
			justify-content: center;
			margin: 50rpx auto;
			color: #ccc;
			border-radius: 10rpx;
		}
		.login-SubName{
			width: 80%;
			margin: 50rpx auto;
			color: #7d64ce;
			font-size: 28rpx;
			display: flex;
			justify-content: space-between;
		}
		.login-logo{
			width: 80%;
			margin: 0 auto;
			margin-top: 100rpx;
			.logo-box{
				display: flex;
				flex-wrap: wrap;
				justify-content: center;
				image{
					width: 60rpx;
					height: 60rpx;
				}
				p{
					display: flex;
					justify-content: center;
					width: 100%;
					font-size: 25rpx;
					margin-top: 10rpx;
				}
			}
		}
		
	}
</style>
