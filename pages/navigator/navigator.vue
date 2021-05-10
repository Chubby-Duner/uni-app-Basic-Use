<template>
	<view>
		<view>导航跳转的学习</view>
		<navigator url="/pages/detail/detail?id=80&age=19">跳转至详情页</navigator>
		<navigator url="/pages/message/message" open-type="switchTab">跳转至信息页</navigator>
		<navigator url="/pages/detail/detail" open-type="redirect">跳转至详情页</navigator>
		<button @click="goDetail">跳转至详情页</button>
		<button @click="goMessage">跳转至信息页</button>
		<button type="primary" @click="redirectDetail()">跳转到详情页并关闭当前页面</button>
		<button type="primary" @click="addToCar">加入购物车</button>
	</view>
</template>

<script>
	export default {
		onUnload() {
			console.log('导航页面卸载了')
		},

		methods: {
			goDetail() {
				uni.navigateTo({ // 有返回
					url: '/pages/detail/detail?id=80&age=19'
				})
			},
			goMessage() {
				uni.switchTab({  // 跳转到 tabBar 页面，并关闭其他所有非 tabBar 页面。 没有返回
					url: '/pages/message/message' // 需在 pages.json 的 tabBar 字段定义的页面路径
				})
			},
			redirectDetail() {
				uni.redirectTo({ // 关闭当前页面，跳转到应用内的某个页面 有返回，但返回首页
					url: '/pages/detail/detail'
				});
			},
			addToCar() {
				uni.$emit('updateCart', {
					id: 10,
					name: '贸易'
				})
			}
		}
	}
</script>

<style>
</style>
