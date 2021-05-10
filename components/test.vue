<template>
	<view id="myView">
		这是test组件 {{num}}
		这是父组件传递过来的数据 {{title}}
		<button @click="sendNum">给父组件传值</button>
		<button type="default" @click="getList()">获取list</button>
	</view>
</template>

<script>
	export default {
		name: "test",
		data() {
			return {
				num: 3,
				intId: null
			};
		},
		props: {
			title: {
				type: String,
				default: ''
			},
			list: {
				type: Array,
				default: () => {
					return []
				}
			}
		},
		onLoad() {
			console.log(this.list,'+++++1111+');
		},
		methods: {
			sendNum() {
				console.log('给父亲传值')
				this.$emit('myEven', this.num)
			},
			getList() {
				console.log(this.list,'++++++');
			}
		},
		beforeCreate() {
			console.log('实例已经开始初始化了')
			console.log(this.num)
		},
		created() {
			console.log('created', this.num)
			// this.intId = setInterval(()=>{
			// 	console.log('执行定时器')
			// },1000)
			console.log(this.list,'-----');
		},
		beforeMount() {
			// console.log('beforemount',document.getElementById('myView'))
		},
		mounted() {
			// console.log('mounted',document.getElementById('myView'))
			console.log(this.list,'++++++');
		},
		destroyed() {
			console.log('组件销毁了')
			clearInterval(this.intId)
		}
	}
</script>

<style>

</style>
