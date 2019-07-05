<template>
	<view class="container">
		<view class="header">
			<!-- 搜索 -->
			<view class="searchwrap">
				<view class="mp-search-box">
					<span class="iconfont icon-htmal5icon25"></span>
					<input class="ser-input" type="text" placeholder="搜索症状/疾病/科室/医院" placeholder-style="color:#666 ;margin:5px 0px;line-height:42px !important;font-size: 16px" @click="showV" />
				</view>
			</view>
			<view class="modal" v-show="show">
				<!-- <view class="modal_V"> -->
					<span @click="hideV">取消</span>
				<!-- </view> -->
			</view>
			<!-- 科室 -->
			<view class="grids division">
				<view class="grid" @tap="toDoctor_list">
					<view class="grid-img">
						<image src="https://askpub.dxycdn.com/2017/06/08/58/7dnpaxuz.png" ></image>
					</view>
					<p class="grid_lable">儿科</p>
				</view>
				<view class="grid" @tap="toDoctor_list">
					<view class="grid-img">
						<image src="https://askpub.dxycdn.com/2017/06/08/00/o0qbdbfi.png" ></image>
					</view>
					<p class="grid_lable">妇产科</p>
				</view>
				<view class="grid" @tap="toDoctor_list">
					<view class="grid-img">
						<image src="https://askpub.dxycdn.com/2017/06/08/01/et2giutm.png" ></image>
					</view>
					<p class="grid_lable">皮肤科</p>
				</view>
				<view class="grid" @tap="toalldepartments">
					<view class="grid-img">
						<span class='iconfont icon-quanbu'></span>
					</view>
					<p class="grid_lable">全部科室</p>
				</view>
			</view>
		</view>	
	<view class="section">
		<!-- 提问 -->
		<view class="finddoctor" @tap="tonew_file">
			<h2>身体小问题？快速问医生</h2>
			<h4>三甲医院主治及以上医师，已解答<span>120万</span>个问题</h4>
			<button type="primary" >立即提问</button>
		</view>
		<!-- 问题 -->
		<view class="questionwrap">
			<view class="kong">
			</view>
				<view class="uni-list-cell" hover-class="uni-list-cell-hover" v-for="item in questionList" :key="item.article_id" >
				<view class="question-list" @tap="toquestionList_datail" :data-qdid="item.article_id">
					<view class="doctor-detail">
						<image class="doctor_img" :src="item.doctor_avatar"></image>
						<span class="doctor_name">{{item.doctor_username}}</span>
						<span class="doctor_fa">{{item.doctor_hospital_name}}</span>
					</view>	
					<view class="question_detail">
						<view class="question_title">{{item.title}}</view>
						<view class="question_text">{{item.content_brief}}</view>	
					</view>	
				</view>
			</view>
		</view>
		
		
		</view>		
	</view>	
</template>

<script>
	export default {
		data() {
			return {
				questionList:'',
				show:false
			}
		},
		onLoad() {
			uni.showLoading({
				title: 'loading',
				mask: false
			});
			uni.request({
				url: '/dpc/view/i/biz/feed?dxa_adplatform=m.dxy.com&page_index=1',
				// url: 'https://www.easy-mock.com/mock/5d1c6741e5897858bd0302ee/index',
				method: 'GET',
				data: {},
				success: res => {
					console.log(res.data.data.items[0].ask_index_article_list);
					this.questionList=res.data.data.items[0].ask_index_article_list
					uni.hideLoading();
				},
				fail: () => {},
				complete: () => {}
			});
		},
		methods: {
			hideV(){
				this.show=false
			},
			showV(){
				this.show=true
			},
			//儿科
			toDoctor_list(){
				uni.navigateTo({
					url: '../Doctor_list/Doctor_list'
				});
			},
			//全部科室
			toalldepartments(){
				uni.navigateTo({
					url: '../alldepartments/alldepartments',
				});
			},
			//提问，问诊
			tonew_file(){
				uni.navigateTo({
					url: '../message/message',
				});
			},
			//问题列表详情
			toquestionList_datail(e){
				let qdid=e.currentTarget.dataset.qdid;
				// console.log(qdid);
				uni.navigateTo({
					url: '../questionList_datail/questionList_datail?qdid='+qdid,
				});
			}
		}
	}
</script>

<style >
@import '../../static/font_icon/iconfont.css';
	/* 模态框 */
	.modal{
		width: 100%;
		height: 100%;
		z-index: 1000;
		background: rgba(255,255,255,.8);
		position: fixed;
		top: 60px;
	}
	.modal span{
		color: #fff;
		position: absolute;
		top: -36px;
		right: 25px;
		font-size: 16px;
	}
	


	.header{
		background: #44b9a3;
	}
	.searchwrap{
		width: 100%;
		background: #00c792;
		padding-top: 20px;
	}
	.mp-search-box{
		box-sizing: border-box;
		margin:0px 20px;
		padding-left: 10px;
		background: #44b9a3;
		border:1px solid #44b9a3 ;
		border-radius: 20px;
		height: 35px;
		overflow: hidden;
	}
	.mp-search-box .ser-input{
		display: inline;
		padding-left:5px ;
		float: left;
		font-size:16px !important;
		line-height:42px !important;
		text-align: left;
		color:#333;		
		width: 85%;
	}
	.icon-htmal5icon25{
		float: left;
		display: inline;
		font-size: 24px;
		line-height: 42px;
		color: #333;
	}
	
	.division {
		background-color: #00c792;
		display: flex;
		/* padding-top: 50px; */
	}
	.grid{
		width: 25%;
		padding: 20px 0 12px 0;
		text-align: center;	
	}
	.grid-img image{
		width: 44px;
		height: 44px;
	}
	.grid_lable{
		line-height: 46px;
		font-size: 18px;
		color: #fff;		
	}
	.finddoctor{
		/* width: 100%; */
		padding: 15px 0px;
		/* background: #0077AA; */
		text-align: center;
	}
	.finddoctor h2{
		font-size: 18px;
		color: #333;
		line-height: 30px;
	}
	.finddoctor h4{
		color: #44b9a3;
		font-size: 14px;
		line-height: 30px;
	}
	.finddoctor h4 span{
		color: #FF0000;
		padding: 0px 5px;
	}
	.finddoctor button{
		font-size: 18px;
		color: #fff;
		background: #EE9900;
		line-height: 45px;
		width: 170px;
		margin-top: 10px;
		text-align: center;
		border-radius: 34px;
	}
	.questionwrap{
		box-sizing: border-box;
		/* background: pink; */
		width: 100%;
	}
	.questionwrap .kong{
		width: 100%;
		height: 15px;
		background: #f4f4f4;
	}
	.question-list{
		padding: 0px 10px;
		width:calc(100% - 20px);
		margin-top: 10px;
	}
	.question-list .doctor-detail{
		display: flex;
		flex-direction: row;
		display: block;
		/* margin-bottom: 5px; */
	}
	.question-list .doctor-detail .doctor_img{
		width: 25px;
		height: 25px;
		border-radius: 50%;
		vertical-align: middle;
	}
	.question-list .doctor-detail .doctor_name{
		/* height: 18px; */
		font-weight: 500;
		color: #00ad7f;
		margin: 0 10px;
		font-size: 14px;
		line-height: 23px;
		overflow: hidden;
	}
	.question-list .doctor-detail .doctor_fa{
		width: 200px;
		/* height: 18px; */
		color: #999;
		font-size: 14px;
		line-height: 23px;
		overflow: hidden;
	}
	.question-list .question_detail {
		padding: 10px 0px; 
		height: 150px;
		overflow: hidden;
	}
	.question-list .question_detail .question_title{
		font-size: 22px;
		color: #333333;
		line-height: 32px;
	}
	.question-list .question_detail .question_text{
		padding: 5px 0px;
		font-size: 15px;
		color: #666;
		line-height: 22px;
		overflow: hidden;
		height: 80px;
	}
	.icon-quanbu{
		font-size:28px;
		color: #fff;
		border: 1px solid #fff;
		border-radius: 50%;
		padding: 8px;

	}
</style>
