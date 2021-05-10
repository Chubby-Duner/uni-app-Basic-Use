<template>
	<view>
		<button type="primary" @click="chooseImg">上传图片</button>
		<image v-for="item in imgArr" :src="item" @click="previewImg(item)"></image>
		<!-- #ifdef H5 -->
		<view>我希望只在h5页面中看见</view>
		<!-- #endif -->
		<!-- #ifdef MP-WEIXIN -->
		<view>我希望只在微信小程序页面中看见</view>
		<!-- #endif -->
	</view>
</template>

<script>
	export default {
		data() {
			return {
				imgArr: []
			}
		},
		methods: {
			chooseImg() {
				// uni.chooseImage 从本地相册选择图片或使用相机拍照。
				uni.chooseImage({
					count: 5, // 最多可以选择的图片张数，默认9。超出5张的限制数量只选取前5张
					success: res => {
						this.imgArr = res.tempFilePaths; // 本地文件路径
						console.log(res);
					}
				})
			},

			previewImg(current) {
				// 预览图片
				uni.previewImage({
					current,
					urls: this.imgArr,
					loop: true,
					indicator: 'default' // 图片指示器样式，可取值："default" - 底部圆点指示器； "number" - 顶部数字指示器； "none" - 不显示指示器。
				})
			}
		},
		onLoad() {
			// #ifdef H5
			console.log('我希望h5中打印')
			// #endif
			// #ifdef MP-WEIXIN
			console.log('我希望微信小程序中打印')
			// #endif
		}
	}
</script>

<style>
	/* h5中的样式 */
	/* #ifdef H5 */
	view {
		color: hotpink;
	}

	/* #endif */
	/* 微信小程序中的样式 */
	/* #ifdef MP-WEIXIN */
	view {
		color: #0000FF;
	}

	/* #endif */
</style>
