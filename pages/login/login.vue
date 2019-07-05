<template>
	<view class="loginwrap">
		<!-- 头部 -->
		<view class="login">
			<view class="l_header">
				<view class="img">
					<image src="https://img1.dxycdn.com/2019/0423/983/3341498255132743445-22.png" ></image>
				</view>
				<view class="l_text">
					<view class="reg_log" @click="showlogin">{{login}}</view>
				</view>
				<view class="l_icon">
					<span class="iconfont icon-remind"></span>
				</view>
			</view>
			<view class="l_bottom">
				<view class="lb-text">
					<p>0</p>
					<p>关注医生</p>
				</view>
				<view class="lb-text">
					<p>0</p>
					<p>医生卡</p>
				</view>
				<view class="lb-text">
					<p>0</p>
					<p>优惠券</p>
				</view>
				<view class="lb-text">
					<p>0</p>
					<p>收藏内容</p>
				</view>
			</view>
		</view>	
		<!-- 模态框 -->
		<view class="modal" v-show="show">
			<view class="modal_log">
				<view class="text">需要登陆	</view>
				<view class="text">快速登陆</view>
				<view class="text">微信登陆	</view>
				<view class="text">	其他方式登陆</view>
				<view class="text" @touchstart="hidelogin">	取消</view>
			</view>
		</view>
		
		
		<!-- 内容 -->
		<view class="content">
			<view class="buy">
				<view class="lb-text">
					<span class="iconfont icon-icon_zaixianwenzhen
"></span>
					<p>我的问诊</p>
				</view>
				<view class="lb-text">
					<span class="iconfont icon-chufang"></span>
					<p>我的处方</p>
				</view>
				<view class="lb-text">
					<span class="iconfont icon-xingzhuanggongnengtubiao-"></span>
					<p>药品订单</p>
				</view>
				<view class="lb-text">
					<span class="iconfont icon-shipin"></span>
					<p>医师讲堂</p>
				</view>
				<view class="lb-text">
					<span class="iconfont icon-zhuye_chengchangjilu"></span>
					<p>成长测评</p>
				</view>
			</view>
		<!-- 私人医生 -->
			<view class="mydoctor">
				<p>私人医生 <span class="num">0</span></p>
				<span>></span>
			</view>
			<!-- 患者信息 -->
			<view class="mydoctor">
				<p>患者信息</p>
				<span>></span>
			</view>
			<!-- 邀请好友 -->
			<view class="mydoctor">
				<p>邀请好友</p>
				<span>></span>
			</view>
		<view class="total">	
			<!-- 设置 -->
			<view class="mydoctor">
				<p>设置</p>
				<span>></span>
			</view>
			<view class="my_kong">
			</view>
			<!-- 用户反馈 -->
			<view class="mydoctor">
				<p>用户反馈</p>
				<span>></span>
			</view>	
		</view>			
		</view>	
		<view class="bottom">
			<h1>严格质控 双重审核</h1>
			<h2>
				<span>三甲以上主治医师</span>
				<span>专家团队 双重审核</span>
			</h2>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				login:"注册/登陆",
				show:false
			}
		},
		methods: {
			hidelogin(){
				this.show=false
			},
			showlogin(){
				this.show=true
			}
		}
	}
</script>

<style>
@import '../../static/font_icon/iconfont.css';
	.loginwrap{
		background: #eaefea;
	}
	.login{
		padding-top: 20px;
	}
	.l_header{
		padding:10px 15px;
		display: flex;
		align-items: center;
	}
	.img{
		flex: 1;
		align-items: center;
	}
	.img image{
		width: 60px;
		height: 60px;
		border-radius: 50%;
	}
	.l_text{
		flex: 2;
		margin-left: -5px;
	}
	.reg_log{
		font-size: 24px;
		color: #000;
		font-weight: 600;
	}
	.l_icon{
		flex: 1;
		position: relative;
	}
	.l_icon .iconfont{
		font-size: 20px;
		color: #000;
		position: absolute;
		top: -40px;
		right: 20px;
	}
	.l_bottom{
		display: flex;
		padding:10px 20px;
		justify-content: space-between;
	}
	.lb-text{
		text-align: center;
		font-size: 14px;
		color: #666;
	}

	/* 模态框 */
	.modal{
		width: 100%;
		height: 100%;
		position: fixed;
		top: 0px;
		z-index: 1000;
		background: rgba(0,0,0,.5);
	}
	.modal_log{
		width: 80%;
		height: 300px;
		background: #fff;
		padding: 0px 20px;
		position: fixed;
		margin: auto ;
		left: 0;
		right: 0;
		top: 0;
		bottom: 0;
		display: flex;
		flex-direction: column;	
		text-align: center;
	}
	.modal_log .text{
		width: 100%;
		flex: 1;
		font-size: 18px;
		color: #00C792;
		line-height: 60px;
	}
	.modal_log .text:nth-of-type(1){
		color: #000;
		border-bottom: 1px solid #D9D9D9;
		font-weight: 600;
	}
	.modal_log .text:nth-of-type(2){
		color: #999;
		font-size: 16px;
	}
	.modal_log .text:nth-of-type(3){
		color: #fff;
		background: #44b9a3;
	}
	
	
	/* 内容 */
	.buy{
		margin-top: 10px;
		display: flex;
		padding:10px 10px;
		justify-content: space-between;
		background: #FFFDEF;
	}
	.buy .lb-text .iconfont{
		font-size: 32px;
	}
	.buy .lb-text:nth-of-type(1) .iconfont{
		color: #DF5000;
	}
	.buy .lb-text:nth-of-type(2) .iconfont{
		color:#576B95;
	}
	.buy .lb-text:nth-of-type(3) .iconfont{
		color: #0A98D5;
	}
	.buy .lb-text:nth-of-type(4) .iconfont{
		color: #F37B1D;
	}
	.buy .lb-text:nth-of-type(5) .iconfont{
		color: #4CD964;
	}
	.buy .lb-text p{
		font-size: 15px;
		color: #000;
	}
	
	.mydoctor{
		display: flex;
		flex-direction: row;
		font-size: 16px;
		line-height: 50px;
		color: #333;
		margin: 12px 0px;
		padding: 0px 10px;
		padding-left: 20px;
		background: #fff;
	}
	.total{
		background: #fff;
	}
	.my_kong{
		margin: 0px 20px;
		height: 1px;
		background: #d2cdcd;
		margin-top: -5px;
	}
	.mydoctor p{
		flex: 10;
		float: left;
	}
	.mydoctor span{
		/* background: #0077AA; */
		text-align: center;
		flex: 1;
	}
	.mydoctor .num{
		float: right
	}
	
	
	.bottom{
		padding: 50px 40px;
		/* background: #007AFF; */
		text-align: center;
	}
	.bottom h1{
		font-size: 16px;
		color: #333;
		font-weight: 800;
		line-height:32px;
	}
	.bottom h2{
		font-size: 14px;
		color: #666;
		font-weight: 500;
		line-height:24px;
	}
	.bottom h2 span:nth-of-type(1){
		margin-right:20px ;
	}
</style>
