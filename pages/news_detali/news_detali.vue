<template>
	<view class="content">
		<view class="title">{{title}}</view>
		<view class="article-content">
			<rich-text class="richText" :nodes="strings"></rich-text>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				title: '',
				strings: ''
			}
		},
		onLoad(e){
			console.log(e);
			uni.request({
				url: 'https://unidemo.dcloud.net.cn/api/news/36kr/'+e.newsId,
				method: 'GET',
				data: {},
				success: res => {
					console.log(res);
					this.title=res.data.title;
					this.strings=res.data.content;
				},
				fail: () => {},
				complete: () => {}
			});
		}
	}
</script>
<style>
	.content{
		padding: 10upx 2%; width: 96%; flex-wrap:wrap;
	}
	.title{
		line-height: 2em;
		font-weight: 700;
		font-size: 38upx;
	}
	.article-content{
		line-height: 2em;
		font-size: 32upx;
	}
</style>
