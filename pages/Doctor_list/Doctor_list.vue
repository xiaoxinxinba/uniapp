<template>
	<view class="doctorlistWrap">
		<view class="doctorlist">
			<view class="header">
				<view class="img">
					<image src="https://img.dxycdn.com/dotcom/2016/10/24/20/ki2je7ts.png" ></image>
				</view>
				<view class="header_text">
					<h5>儿科</h5>
					<p>小儿发烧、咳嗽、哮喘、流鼻涕、腹泻、黄疸、辅食、生长发育、疫苗接种、儿童用药、幼儿急疹</p>	
				</view>
			</view>
			<view class="kong">
				<view class="k_text">为你推荐的医生</view>
			</view>
			<view class="doctorlist-cell" v-for="item in doctorlist" :key="item.doctor.id">
				<view class="d_list" >
					<view class="img">
						<image :src="item.doctor.avatar" ></image>
					</view>
					<view class="d_text">
						<h3>{{item.doctor.nickname}} <span>{{item.doctor.job_title_name}}</span></h3>
						<h5>{{item.doctor.section_name}}  {{item.doctor.hospital_name}}</h5>
						<p>{{item.doctor.self_desc}}</p>	
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
				doctorlist:[]
			}
		},
		onLoad() {
			uni.request({
				url: 'https://www.easy-mock.com/mock/5d1c6741e5897858bd0302ee/doctor_list',
				method: 'GET',
				data: {},
				success: res => {
					// console.log(res.data.data.items)
					this.doctorlist=res.data.data.items
					// console.log(this.doctorlist)
				},
				fail: () => {},
				complete: () => {}
			});
		},
		methods: {
			
		}
	}
</script>

<style>
	.doctorlist .header{
		display: flex;
		flex-direction: row;
		padding: 10px 0px;
		/* background: #795DA3; */
		height: 100px;
		overflow: hidden;
		font-size: 16px;
		padding: 0px 10px;
	}
	.doctorlist .header .img{
		flex: .5;
	}
	.header .img image{
		width: 50px;
		height: 50px;
	}
	.doctorlist .img image{
		border-radius: 50%;
		margin-top: 20px;
	}
	.doctorlist .header .header_text{
		overflow: hidden;
		margin-left: 10px;
	}
	.doctorlist .header .header_text h5{
		font-size: 18px;
		color: #000000;
		line-height: 28px;
	}
	.doctorlist .header .header_text p{
		font-size: 16px;
		color: #666;
		padding: 5px 0px;
		overflow: hidden;
		line-height: 20px;
	}
	
	.kong .k_text{
		background: #f4f4f4;
		width: 100%;
		font-size: 16px ;
		padding-left: 20px;
		color: #666;
		line-height: 36px ;
	}
		
	
	.d_list{	
		display: flex;
		flex-direction: row;
		padding: 10px 10px;
		/* background: #795DA3; */
		/* height: 130px; */
		overflow: hidden;
		font-size: 16px;
		padding: 0px 10px;
	}
	.d_list .img{
		flex: .5;
	}
	.d_list .img image{
		width: 44px;
		height: 44px;
	}
	.d_list .d_text{
		overflow: hidden;
		margin: 10px 0px;
		margin-left:10px;
	}
	.d_list .d_text h3{
		font-size: 18px;
		color: #000000;
		line-height:30px;
	}
	.d_list .d_text h3 span{
		font-size: 15px;
		color: #333;
		margin-left: 5px;
	}
	.d_list .d_text h5{
		font-size: 15px;
		color: #333;
		line-height: 24px;
	}
	.d_list .d_text p{
		font-size: 14px;
		color: #666;
		line-height: 20px;
		overflow: hidden;
	}
</style>
