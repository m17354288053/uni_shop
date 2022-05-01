<template>
		<view class="recommend-list">
			<view class="recommend-item" v-for="(p,index) in product " :key="index">
				<image :src="p.imgURL"></image>
				<view class="intro">{{p.productIntro}}</view>
				<view style="display: flex;justify-content: space-between;">
					<view style="color: #E63214;font-size: 32rpx;margin-top: 28rpx;margin-left: 20rpx;">￥{{p.productPrice}}</view>
					<image style="height: 54rpx; width: 54rpx;margin-right: 30rpx;" src="../../static/img/icon_cart3.png"></image>
				</view>
			</view>
		</view>
</template>

<script>
	export default {
		props:["product"]
	}
</script>

<style scoped lang="scss">
	.recommend-list {
		display: flex;
		flex-wrap: wrap;
		column-count: 2;
		column-gap: 9rpx;
		.recommend-item {
			width: 346rpx;
			height: 496rpx;
			image {
				width: 306rpx;
				height: 306rpx;
				margin: 20rpx 20rpx 10rpx 20rpx;
			}
			.intro {
				margin: 10rpx 20rpx 0 20rpx;
				font-size: 26rpx;
			}
		}
	}
</style>
