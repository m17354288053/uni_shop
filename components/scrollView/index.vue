<template>
	<!-- 公共横向滚动组件 -->
	<!-- 新品列表 -->
	<view class="new-product-list">
		<scroll-view scroll-x="true" class="scroll-view_H">
			<view class="new-product-item" v-for="(p , index) in product" :key="index">
				<image class="new-product-img" :src="p.imgURL"></image>
				<view class="new-product-intro">
					{{p.productIntro}}
				</view>
				<view class="new-prouct-buttom">
					<view class="new-product-price">￥{{p.productPrice}}</view>
					<image class="new-product-add" src="../../static/img/icon_add.png"></image>
				</view>
			</view>
		</scroll-view>
	</view>
</template>

<script>
	export default {
		props: ["product"]
	}
</script>

<style scoped lang="scss">
	
	.scroll-view_H::-webkit-scrollbar {
		display: none;
	}
	
	// 新品展示
	.new-product-list {
		margin-left: 20rpx;
		margin-top: 42rpx;
		margin-right: 20rpx;
		.scroll-view_H {
			width: 100%;
			white-space: nowrap;
			padding-right: 20rpx;
			.new-product-item {
				margin-left: 12rpx;
				margin-bottom: 46rpx;
				width: 220rpx;
				display: inline-block;

				.new-product-img {
					width: 220rpx;
					height: 220rpx;
					border-radius: 8rpx;
				}

				.new-product-intro {
					width: 196rpx;
					height: 68rpx;
					font-size: 24rpx;
					color: #242424;
					margin-left: 12rpx;
					margin-right: 12rpx;

					// 控制文字溢出
					white-space: normal;
					overflow: hidden;
					text-overflow: ellipsis;
				}

				.new-prouct-buttom {
					display: flex;
					justify-content: space-between;

					.new-product-price {
						font-size: 32rpx;
						margin-left: 12rpx;
						color: #E63214;
					}

					.new-product-add {
						width: 36rpx;
						height: 36rpx;
						margin-right: 12rpx;
					}
				}
			}
		}
	}
</style>
