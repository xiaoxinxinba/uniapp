<template>
	<view class="container">
		<view class="text">
			<textarea value="" placeholder="请描述你的年龄、性别、症状及就诊经历，便于医生进行准确分析，我们会确保你的隐私" placeholder-style="font-size:18px;color:#999;line-height:25px;width:100%;" maxlength="500"/>
			<view class="upload">
				<view class="load">
					<image src="../../static/image/xj.png" ></image>
				</view>
				<view class="text">
					<p>上传图片说明病情</p>
					<p>可上传9张</p>
				</view>
			</view>
		</view>
		<button type="primary">写好了</button>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		onLoad() {
			
		},
		methods: {
			
		}
	}
</script>

<style>
	.container{
		background: #f4f4f4;
	}
	.text{
		padding: 10px 20px;
		/* height: 250px; */
		background: #FFFFFF;
	}
	.text textarea{
		width: 100%;
		overflow: hidden;
		height: 200px;
		font-size: 20px;
		color: #333;
		line-height: 25px;
	}
	button{
		background: #00c792;
		font-size: 18px;
		line-height: 48px;
		margin: 20px 20px;
	}
	.text .upload{
		margin-top: 20px;
		/* background: pink; */
		padding: 10px 0px;
		display: flex;
	}
	.text .upload .load{
		flex: 1;
		width: 32%;
		height: 100px;
		border: 1px solid #D9D9D9;
		text-align: center;
		position: relative;
	}
	.text .upload .load image{
		position: absolute;
		width: 38px;	
		height: 38px;	
		top: 30%;
		left: 30%;
	}
	.text .upload .text{
		flex: 2;
		color: #999;
		margin-top: 10px;
		line-height: 25px;
		font-size: 15px;
	}
</style>
