<!--
 * @Descripttion: 
 * @version: 
 * @Author: woxiaoyao
 * @Date: 2020-09-28 18:46:30
 * @LastEditTime: 2020-09-30 16:21:08
-->
<template>
	<view>
		<view class="header">
			<image class="back" src="../../static/black-back.png" mode="" @click='back'></image>
		</view>
		<container title='基础式'>
			<u-swiper :list="base_lsit" name="imgUrl"></u-swiper>
		</container>
		<container title='卡片式'>
			<u-swiper :list="base_lsit" name="imgUrl" :effect3d="true"></u-swiper>
		</container>
	</view>
</template>

<script>
	import api from '../../api/index.js'
	import container from '../../components/container/index.vue'
	export default {
		components: {
			container,
		},
		data() {
			return {
				base_lsit: []
			}
		},
		onLoad() {
			this.getBase()
		},
		methods: {
			getBase() {
				api.base(100).then(res => {
					this.base_lsit = res
				})
			},
			clickItem(data) {
				console.log(data)
			},
			back() {
				uni.redirectTo({
					url: '/pages/index/index',
				})
			}
		}
	}
</script>

<style lang="scss" scoped>
	.header {
		margin-top: 40rpx;
		display: flex;
		align-items: center;
		height: 80rpx;
		padding-left: 20rpx;
		margin-bottom: 30rpx;

		.back {
			width: 30rpx;
			height: 30rpx;
		}
	}
</style>
