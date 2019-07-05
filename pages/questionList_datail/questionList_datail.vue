<template>
	<view>
		<view class="q_detail">
			<view class="qd_title">
				<h1>一吹风就流泪？眼科医生告诉你怎么回事</h1>
				<p>作者:<span>罗荃</span><i>2015-09-23</i></p>
			</view>
			<image src="//img.dxycdn.com/dotcom/2015/09/23/26/lxscd9vh.jpg"></image>
			<view class="text">
				<p>秋风凛冽，吹得小张眼睛都不舒服，眼角也不自主地湿润起来，眨眨眼还流出眼泪来了。</p>
				<p>小张有点纳闷，上网一查，发现「迎风流泪」的相关词条还不少，而且，好多人说这是肝肾不好的表现呢。怎么办，要去看病吗？</p>
				<h2>迎风流泪是病吗？</h2>
				<p>其实，人的眼睛时刻都在「流泪」。我们之所以感觉不到，是因为平常分泌的泪液量很少，仅仅储存在眼皮和眼珠子之间的缝隙里，叫做基础泪液。在眨眼的同时，眼睑会轻轻地将泪液均匀涂抹在眼睛表面，形成一层「泪膜」，滋润眼睛。</p>
				<p>眼球是个「娇气」的器官，尤其是眼球表面的细胞，对于外界环境有很强的感知能力。一旦受到外界的刺激，泪液量就会明显增加，这时分泌的泪液叫反射泪液，可以起到保护眼睛的作用。</p>
				<p>受到刺激的程度不同，泪液的量也不同，少的时候可以没有任何感觉，多的时候可以像哭泣一样，泪液量特别大。</p>
				<p>常见的刺激包括了吹风、异物、刺激性气体等。吹的风越大，吹得越久，流的泪自然会越明显。</p>
				<p>那么，我们是否可以理解为，迎风流泪是正常现象，完全不需要担心呢？</p>
				<p>不，我们不能绝对地这么说。有些患者眼表面细胞的敏感性增加了，眼睛对外界刺激容易处于一种「反应过激」的状态，使得反射性分泌的泪液偏多。这个现象可能和一些眼表面的疾病有关。</p>
				<h2>哪些人更容易迎风流泪？</h2>
				<p><strong>1. 干眼患者</strong></p>
				<p>对于干眼患者来说，吹风带来的最直接影响是加强了泪液的蒸发，导致眼睛表面干燥得更明显。这种干燥同样也会刺激眼表面细胞，导致反射性泪液的快速分泌和流出。另外，干眼患者眼表面的炎症因子增多，也可能导致眼睛更「敏感」。</p>
				<p>由于中老年人群中干眼比较常见，所以，迎风流泪的现象也比较普遍。而年轻人目前在电脑前工作时间久了，干眼的表现也比较明显，可以增加眨眼次数缓解干眼症状。</p>
				<p><strong>2. 结膜炎等眼表疾病患者</strong></p>
				<p>眼表面组织的各种急性或慢性的炎症会明显增加眼睛的敏感度。</p>
				<p>另外，有些患者眼表面分泌和储存的泪液本来就偏多了，比如倒睫导致角膜上皮缺损，或者泪道不通畅导致泪液无法顺利地排出。</p>
			</view>
		</view>
			<!-- 方法 -->
			
	
	</view>
</template>

<script>


export default {
    data() {
        return {
		}
	},
    components: {
	},
	onLoad(option) {
		
		//详情
		uni.request({
			// url: 'https://www.easy-mock.com/mock/5d1c6741e5897858bd0302ee/index',
			url: 'https://www.easy-mock.com/mock/5d1c6741e5897858bd0302ee/index_detail/'+option.qdid,
			method: 'GET',
			success: res => {
				console.log(res);
			},
			fail: () => {},
			complete: () => {}
		});
		//解决方法
		uni.request({
			url: 'https://www.easy-mock.com/mock/5d1c6741e5897858bd0302ee/method',
			method: 'GET',
			data: {},
			success: res => {
				// console.log(res)
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
	.q_detail{
		padding: 10px 10px;
		/* background: pink; */
	}
	.q_detail .qd_title h1{
		font-size: 24px;
		line-height: 36px;
		margin-top: 20px;
	}
	.q_detail .qd_title p{
		font-size: 16px;
		color: #666;
	}
	.q_detail .qd_title p span{
		padding: 0px 10px;
		color:#7e57b2;
		/* padding-right: 10px; */
	}
	.q_detail image{
		width: 100%;
		height: 190px;
		margin-bottom: 5%;
	}
	.q_detail .text p{
		font-size: 16px;
		line-height: 30px;
		color: #333;
		padding-bottom: 10px;
	}
	.q_detail .text h2{
		font-size: 18px;
		color: #000;
		padding: 10px 0px;
	}
</style>
