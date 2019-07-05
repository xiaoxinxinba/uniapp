<template>
	<view class="uni-tab-bar">
		<scroll-view id="tab-bar" class="uni-swiper-tab" scroll-x :scroll-left="scrollLeft">
			<view v-for="(tab,index) in tabBars" :key="tab.id" class="swiper-tab-list" :class="tabIndex==index ? 'active' : ''"
			 :id="tab.id" :data-current="index" @click="tapTab">{{tab.name}}</view>
		</scroll-view>
		<swiper class="swiper" :current="tabIndex" @change="changeTab" :duration="300">
			<swiper-item v-for="i in [0,1,2,3,4]" :key="i">
				<view class="uni-media-list">
					<scroll-view :scroll-top="scrollTop" scroll-y="true" class="scroll-Y"  @scroll="scroll">
						<view id="demo1" class="scroll-view-item" v-for="tab in newsitems" :key="tab.id">
							<image class="uni-media-list-logo" :src="tab.cover_small" mode="widthFix"></image>
							<view class="uni-media-list-body">
								<view class="uni-media-list-text-top">{{tab.title}}</view>
								<view class="uni-media-list-text-bottom uni-ellipsis">{{tab.content_brief}}</view>
							</view>		
						</view>   
					</scroll-view>
				</view> 
			</swiper-item>
		</swiper>
	</view>
</template>
<script>
	export default {
		components: {
		},
		data() {
			return {
				scrollLeft: 0,
				isClickChange: false,
				tabIndex: 0,
				newsitems: [],
				tabBars: [],
				scrollTop: 0,
				old: {
					scrollTop: 0
				}
			}
		},
		onLoad() {
			uni.showLoading({
				title: 'loading',
				mask: false
			});
			//科普导航
			uni.request({
				url: 'https://www.easy-mock.com/mock/5d1c6741e5897858bd0302ee/api',
				method: 'GET',
				data: {},
				success: res => {
					this.tabBars = res.data.data.items
					console.log(this.newsitems)
					uni.hideLoading();
				},
				fail: () => {},
				complete: () => {}
			});
			//科普资料
			uni.request({
				url: 'https://www.easy-mock.com/mock/5d1c6741e5897858bd0302ee/kepu',
				method: 'GET',
				data: {},
				success: res => {
					// console.log(res.data.data.items)
					this.newsitems=res.data.data.items
					console.log(this.newsitems)
					uni.hideLoading();
				},
				fail: () => {},
				complete: () => {}
			});	
		},
		methods: {
			scroll: function(e) {
            this.old.scrollTop = e.detail.scrollTop
			},
			async changeTab(e) {
				let index = e.target.current;
				this.tabIndex = index; //一旦访问data就会出问题
			},
			async tapTab(e) { //点击tab-bar
				// console.log(e)
				let tapTabIndex = e.target.dataset.current;
				// console.log(tabIndex)
				//赋值
				this.tabIndex = tapTabIndex;
			}
		}
	}
</script>

<style>
	uni-page-body{
		height: 100%;
	}
	.uni-swiper-tab{
		background: #44b9a3;
		
	}
	.swiper-tab-list{
		font-size: 18px !important;
	}
	.uni-tab-bar .active{
		color: #fff !important;	
	}
	.swiper{
		height: 100% !important;
	}
	.scroll-Y{
		display: flex;
		height: 1100upx;
		overflow-y: scroll;
	} 	
	.scroll-view-item{
		display: flex;
		margin: 10px 0px;
		align-items: center;
		border-bottom: 1px solid #D9D9D9;
	}
	.uni-media-list-logo{
		width: 100%;
		flex: .5;
	}
	.uni-media-list-body{
		flex: 2.5;
		/* background: pink; */
		height: 100%!important;
	}
	.uni-media-list-text-top{
		font-size: 16px;
		color: #333;
		line-height: 20px;
		padding: 5px 0px;
	}
	.uni-media-list-text-bottom{
		font-size: 14px;
		color: #666;
		line-height: 20px;
		padding: 5px 0px;
	}
</style>
