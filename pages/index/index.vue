<template>
	<view class="wrap">
		<view class="header">
			轮播组件
		</view>
		<view class="item" @click="toBase">
			基础用法
		</view>
		<view class="item" @click="toCustom">
			自定义
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {

			}
		},
		methods: {
			toBase() {
				console.log('to')
				uni.redirectTo({
					url: '/pages/base/base',
				})
			},
			toCustom() {
				console.log('to')
				uni.redirectTo({
					url: '/pages/custom/custom',
				})
			},
		}
	}
</script>

<style lang="scss" scoped>
	.wrap {
		padding: 140rpx 40rpx 40rpx 40rpx;

		.header {
			color: #909ca2;
			font-size: 24rpx;
			letter-spacing: 4rpx;
		}

		.item {
			display: -webkit-box;
			display: -webkit-flex;
			display: flex;
			-webkit-box-align: center;
			-webkit-align-items: center;
			align-items: center;
			height: 40px;
			padding: 0 15px;
			margin-bottom: 15px;
			font-size: 12px;
			letter-spacing: 4rpx;
			background-color: #f7f7f7;
			border-radius: 40px;
			margin-top: 30rpx;
		}
	}
</style>
