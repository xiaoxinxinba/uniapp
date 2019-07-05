<template>
	<view class="department_wrap">
		<view class="department_list">
			<view class="list_cell" @tap="toDoctor_list" v-for="item in depList" :key="item.id">
				<view class="d_list">
					<view class="img">
						<image :src="item.cover_url" ></image>
					</view>
					<view class="d_text">
						<h5>{{item.name}}</h5>
						<p>{{item.description}}</p>	
					</view>
					<view class="d_num">
						<span>{{item.member_count}}位医生 ></span>
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
				depList:[],
			}
		},
		onLoad(){
			// console.log(1)
			uni.request({
				url: '/dpc/view/i/sectiongroup/list?dxa_adplatform=m.dxy.com&page_index=1&items_per_page=10&key=sectionList',
				method: 'GET',
				data: {},
				success: res => {
					console.log(res.data.data.items)
					this.depList=res.data.data.items;
					uni.hideLoading();
				},
				fail: () => {},
				complete: () => {}
			});
		},
		methods: {
			toDoctor_list(){
				uni.navigateTo({
					url: '../Doctor_list/Doctor_list',
				});
			}
		}
	}
</script>

<style>
	.d_list{
		display: flex;
		flex-direction: row;
		padding: 10px 10px;
		/* background: #795DA3; */
		height: 100px;
		overflow: hidden;
		font-size: 16px;
	}
	.d_list .img{
		flex: .5;
	}
	.d_list .img image{
		width: 50px;
		height: 50px;
		border-radius: 50%;
		margin-top: 20px;
	}
	.d_list .d_text{
		/* float: left; */
		flex: 2.5;
		overflow: hidden;
		margin: 0px 10px;
	}
	.d_list .d_text h5{
		font-size: 20px;
		color: #000000;
		line-height: 28px;
	}
	.d_list .d_text p{
		font-size: 18px;
		color: #666;
		padding: 7px 0px;
		overflow: hidden;
	}
	.d_list .d_num{
		flex: 1;
		font-size: 14px;
		color: #666666;
		padding-top: 40px;
	}
</style>
