<template>
	<view>
		<view class="nav_kepu" >
			<wuc-tab :tab-list="tabList" :tabCur.sync="TabCur" @change="tabChange" tabStyle='font-size:16px;background:#44b9a3;line-height:50px ;color:#333;padding:0px 10px;height:50px;' selectClass="text-white" ></wuc-tab>
		</view>
	</view>
</template>

<script>
import WucTab from '@/components/wuc-tab/wuc-tab.vue';
	export default {
		data() {
			return {
			  TabCur: 0,
			  tabList:[],
			}
		},
		components: {
			WucTab ,
		},
		onLoad() {
			uni.request({
				url: 'https://www.easy-mock.com/mock/5d1c6741e5897858bd0302ee/api',
				method: 'GET',
				data: {},
				success: res => {
					// console.log(res.data.data.items);
					// this.menus=res.data.data.items;
					this.tabList=res.data.data.items
				},
				fail: () => {},
				complete: () => {}
			});
		},
		methods: {
			tabChange(index) {
			    this.TabCur = index;
			},
		}
	}
</script>
<style>

</style>
