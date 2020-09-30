<template>
	<view class="container">
		<view class="header">
			<image class="back" src="../../static/black-back.png" mode="" @click='back'></image>
		</view>
		<view class="content">
			<u-swiper :list="list" :haveSlot="true" :effect3d="true" mode="none" @change='change'>
				<template v-slot="{elem}">
					<view class="tab ">
						<image class="tab-img" :src="elem.imgUrl" mode=""></image>
						<text class="tab-title f-bold f34 lb-6">{{elem.label}}</text>
						<view class="tab-tag">{{elem.munber}}个推荐地点</view>
					</view>
				</template>
			</u-swiper>
			<view class="detail">
				<view class="title">
					<text>体验地</text>
				</view>
				<u-swiper :list="d_list" :haveSlot="true" mode="none">
					<template v-slot="{elem}">
						<view class="detail-wrap">
							<view class="detail-item" v-for="(item,i) in elem" :key='i'>
								<image :src="item.imgUrl" mode=""></image>
								<view class="item-text">{{item.label}}</view>
							</view>
						</view>
					</template>
				</u-swiper>
			</view>
		</view>
	</view>
</template>

<script>
	import api from '../../api/index.js'
	export default {
		created() {
			this.getList()
		},
		data() {
			return {
				list: [],
				d_list: []
			}
		},
		methods: {
			getList() {
				api.custom().then(res => {
					this.list = res
					this.d_list = res[0].child
				})
			},
			change(elem) {
				this.d_list = this.list[elem].child
			},
			back() {
				uni.navigateTo({
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

		.back {
			width: 30rpx;
			height: 30rpx;
		}
	}

	.content {
		margin-top: 30rpx;
		background-color: #FFFFFF;

		.tab {
			width: 100%;
			height: calc(100% - 20rpx);
			margin-bottom: 20rpx;
			position: relative;
			border-radius: 8rpx;
			background-color: #000;
			box-shadow: 0 0 14rpx 0 rgba(0, 0, 0, 0.1);

			.tab-img {
				width: 100%;
				height: 100%;
				border-radius: 8rpx;
				opacity: 0.6;
				box-shadow: 0 6px 6px rgba(0, 0, 0, .15);
			}

			.tab-title {
				position: absolute;
				top: 70rpx;
				left: 50%;
				transform: translateX(-50%);
				color: #fff;
			}

			.tab-tag {
				position: absolute;
				top: 120rpx;
				left: 50%;
				transform: translateX(-50%);
				padding: 2rpx 16rpx;
				font-size: 20rpx;
				letter-spacing: 2rpx;
				background-color: #FAB714;
				border-radius: 14rpx;
			}
		}

		.detail {
			margin-top: 20rpx;
			padding: 10rpx;

			.title {
				height: 48rpx;
				line-height: 48rpx;
				font-size: 34rpx;
				font-weight: 600;
				color: rgba(32, 39, 47, 1);
				letter-spacing: 4rpx;
				margin-left: 10rpx;
				margin-bottom: 20rpx;
			}

			.detail-wrap {
				display: flex;
				flex-wrap: wrap;
				justify-content: flex-start;
				padding-left: 10rpx;

				.detail-item {
					width: 230rpx;
					margin-right: 10rpx;

					image {
						width: 100%;
						height: 120rpx;
						border-radius: 6rpx;
					}

					.item-text {
						margin-top: 6rpx;
						margin-bottom: 12rpx;
						font-size: 24rpx;
						letter-spacing: 2rpx;
					}
				}
			}
		}
	}
</style>
