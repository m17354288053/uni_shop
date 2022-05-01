<template>
	<view>

		<!-- 头部导航栏 -->
		<view class="uni-navbar">
			<image src="../../static/img/home/background_header.png" style="height: 100%;width: 100%;"></image>
			<view class="uni-top-navbar">
				<view class="icon-address">
					<image src="../../static/img/home/navbar/icon_adress.png"></image>
					<view class="uni-address">{{address}}</view>
				</view>
				<view class="uni-logo">
					{{logo}}
				</view>
			</view>
			<!-- 头部搜索栏 -->
			<view class="topBar">
				<view class="search-bar">
					<image class="icon-search" src="../../static/img/home/icon_serach.png"></image>
					<input type="text" class="search-text" placeholder="搜索商品名称" maxlength="20">
				</view>
				<image class="icon-qrcode" src="../../static/img/home/icon_qrcode.png"></image>
			</view>
		</view>

		<!-- 轮播图 -->
		<view class=".uni-carousel">
			<swiper :circular="true" :indicator-dots="true" indicator-color="#FFFFFF" :autoplay="true" :interval="3000"
				:duration="1000" :disable-touch="true">
				<swiper-item>
					<view class="swiper-item">
						<image src="../../static/img/home/carousel/矩形 60.png" style="height: 100%;width: 100%;"></image>
					</view>
				</swiper-item>
				<swiper-item>
					<view class="swiper-item">
						<image src="../../static/img/home/carousel/矩形 60.png" style="height: 100%;width: 100%;">
					</view>
				</swiper-item>
				<swiper-item>
					<view class="swiper-item">
						<image src="../../static/img/home/carousel/矩形 60.png" style="height: 100%;width: 100%;">
					</view>
				</swiper-item>
			</swiper>
		</view>

		<!-- 商品分类 -->
		<view class="category-list">
			<view class="category-item">
				<image class="category-img" src="../../static/img/home/category/icon_normal.png"></image>
				<view class="category-text">平价菜场</view>
			</view>
			<view class="category-item">
				<image class="category-img" src="../../static/img/home/category/icon_egg.png"></image>
				<view class="category-text">鲜肉蛋禽</view>
			</view>
			<view class="category-item">
				<image class="category-img" src="../../static/img/home/category/icon_friult.png"></image>
				<view class="category-text">缤纷水果</view>
			</view>
			<view class="category-item">
				<image class="category-img" src="../../static/img/home/category/icon_milk.png"></image>
				<view class="category-text">牛奶面点</view>
			</view>
			<view class="category-item">
				<image class="category-img" src="../../static/img/home/category/icon_oil.png"></image>
				<view class="category-text">粮油速食</view>
			</view>
			<view class="category-item">
				<image class="category-img" src="../../static/img/home/category/icon_coupon.png"></image>
				<view class="category-text">领券中心</view>
			</view>
			<view class="category-item">
				<image class="category-img" src="../../static/img/home/category/icon_store.png"></image>
				<view class="category-text">积分商城</view>
			</view>
			<view class="category-item">
				<image class="category-img" src="../../static/img/home/category/icon_group buy.png"></image>
				<view class="category-text">每日团购</view>
			</view>
		</view>

		<!-- 新品尝鲜 -->
		<view class="uni-fire">
			<!-- 顶部 -->
			<view class="header">
				<view class="header-left">
					<image src="../../static/img/home/fire/icon_fire.png"></image>
					<view class="header-left-text">新品尝鲜</view>
				</view>
				<view class="header-right">
					<view class="header-right-text">更多</view>
					<image src="../../static/img/home/icon_right.png"></image>
				</view>
			</view>
			<scrollView :product="fireProduct"></scrollView>
		</view>

		<!-- 优惠discount -->
		<view class="discount">
			<view class="group-buying">
				<view style="margin-top: 54rpx;">
					<view style="font-size: 40rpx;font-weight: bold;margin-left: 32rpx;">团购</view>
					<view style="color: #B1B1B1;font-size: 24rpx;margin-left: 32rpx;margin-top: 22rpx;">团购更优惠</view>
				</view>
				<image src="../../static/img/home/img_group buy.png"></image>
			</view>
			<view class="coupon">
				<view style="margin-top: 54rpx;">
					<view style="font-size: 40rpx;font-weight: bold;margin-left: 32rpx;">领券中心</view>
					<view style="color: #B1B1B1;font-size: 24rpx;margin-left: 32rpx;margin-top: 22rpx;">领取您的优惠券</view>
				</view>
				<image src="../../static/img/home/img_cupon.png"></image>
			</view>
		</view>
		
		<!-- 限时折扣 -->
		<view class="uni-fire">
			<!-- 顶部 -->
			<view class="header">
				<view class="header-left">
					<image src="../../static/img/home/discountProduct/icon_flash.png"></image>
					<view class="header-left-text">限时折扣</view>
					<view class="">
						
					</view>
				</view>
				<view class="header-right">
					<view class="header-right-text">更多</view>
					<image src="../../static/img/home/icon_right.png"></image>
				</view>
			</view>
			<scrollView :product="discountProduct"></scrollView>
		</view>
		
		<!-- 推荐商品 -->
		<view class="recommend">
			<view style="font-size: 40rpx;font-weight: bold;margin-bottom: 46rpx;">猜你喜欢</view>
				<recommendProduct :product="recommendProduct"></recommendProduct>
		</view>
		
		<!-- 底部bottom -->
		<view class="bottom">
			—— 我是有底线的 ——
		</view>
		
	</view>
</template>

<script>
	import scrollView from '../../components/scrollView/index.vue'
	import recommendProduct from '../../components/recommendProduct/index.vue'
	export default {
		data() {
			return {
				address: '香丽花园',
				logo: 'LOGO',
				// 新品尝鲜
				fireProduct:[
					{
						imgURL:'../../static/img/home/fire/矩形 82.png',
						productIntro: '猪五花肉块 1kg 免切精五花肉带...',
						productPrice: '39.00'
					},
					{
						imgURL:'../../static/img/home/fire/矩形 83.png',
						productIntro: '城市厨房 澳洲牛肉卷肥牛卷450...',
						productPrice: '39.00'
					},
					{
						imgURL:'../../static/img/home/fire/矩形 84.png',
						productIntro: '青岛活冻大黄花鱼1500g 3条 袋...',
						productPrice: '39.00'
					},
					{
						imgURL:'../../static/img/home/fire/矩形 85.png',
						productIntro: '这是商品名称这是商品名称',
						productPrice: '39.00'
					},
				],
				
				// 限时折扣
				discountProduct: [
					{
						imgURL:'../../static/img/home/discountProduct/矩形 89.png',
						productIntro: '四川蒲江精品红心猕猴桃',
						productPrice: '39.00'
					},
					{
						imgURL:'../../static/img/home/discountProduct/矩形 90.png',
						productIntro: '沙窝林子沙窝萝卜小沙沃村现拔现...',
						productPrice: '39.00'
					},
					{
						imgURL:'../../static/img/home/discountProduct/矩形 91.png',
						productIntro: '【精品盒装】松仁玉米 350g/盒',
						productPrice: '39.00'
					},
					{
						imgURL:'../../static/img/home/discountProduct/矩形 92.png',
						productIntro: '这是商品名称这是商品名称',
						productPrice: '39.00'
					},
				],
				
				// 推荐商品
				recommendProduct: [
					{
						imgURL: '../../static/img/home/recommendProduct/矩形 99.png',
						productIntro: '冷冻千丝万缕面线虾 250g*2件 共20只 油炸...',
						productPrice: '39.00'
					},
					{
						imgURL: '../../static/img/home/recommendProduct/矩形 102.png',
						productIntro: '华都食品 鸡翅中 1000g/袋 烧烤食材 ',
						productPrice: '39.00'
					},
					{
						imgURL: '../../static/img/home/recommendProduct/矩形 105.png',
						productIntro: '正大（CP）凝香骨连 800g 骨肉相连',
						productPrice: '39.00'
					},
					{
						imgURL: '../../static/img/home/recommendProduct/矩形 106.png',
						productIntro: '宿迁擀面皮牛肉饼冷冻咖喱煎饼儿童早餐食品',
						productPrice: '39.00'
					},
				]
			}
		},
		components: {
			scrollView,
			recommendProduct
		},
		onLoad() {

		},
		methods: {

		}
	}
</script>

<style scoped lang="scss">
	// 导航栏
	.uni-navbar {
		height: 480rpx;
		width: 750rpx;
		position: relative;

		// 顶部LOGO和地址
		.uni-top-navbar {
			width: 100%;
			float: left;
			top: 88rpx;
			position: absolute;
			display: flex;
			align-items: center;

			.icon-address {
				display: flex;
				align-items: center;

				image {
					height: 52rpx;
					width: 52rpx;
					margin-left: 20rpx;
				}

				.uni-address {
					color: #FFFFFF;
					font-size: 28rpx;
					margin-left: 5rpx;
				}
			}

			.uni-logo {
				height: 38rpx;
				width: 92rpx;
				font-size: 32rpx;
				left: 331rpx;
				color: #FFFFFF;
				margin-left: 142rpx;
				font-weight: bold;
			}
		}

		// 头部搜索栏
		.topBar {
			width: 100%;
			float: left;
			position: absolute;
			top: 188rpx;
			display: flex;
			height: 64rpx;
			align-items: center;
			background-color: #E63214;

			.search-bar {
				height: 64rpx;
				width: 620rpx;
				margin-left: 20rpx;
				background-color: #FFFFFF;
				border-radius: 34rpx;
				display: flex;
				align-items: center;

				.icon-search {
					height: 48rpx;
					width: 48rpx;
					margin-left: 32rpx;
				}

				.search-text {
					color: #B1B1B1;
					font-size: 28rpx;
					margin-left: 9rpx;
				}
			}

			.icon-qrcode {
				height: 48rpx;
				width: 48rpx;
				margin-left: 26rpx;
			}
		}
	}

	// 轮播图
	.uni-carousel {
		height: 304rpx;
		width: 100%;
		position: absolute;
		top: 284rpx;
		margin-left: 20rpx;

		.swiper-item {
			width: 710rpx;
			height: 100%;
		}
	}

	// 商品分类
	.category-list {
		padding-top: 100rpx;
		width: 688rpx;
		display: flex;
		flex-wrap: wrap;
		margin-left: 32rpx;
		margin-right: 32rpx;
		column-count: 4;
		column-gap: 90rpx;

		.category-item {
			margin-top: 40rpx;

			.category-img {
				width: 104rpx;
				height: 104rpx;
			}

			.category-text {
				color: #242424;
				font-size: 24rpx;
				left: 33rpx;
				margin-top: 14rpx;
			}
		}
	}


	// 新品推荐
	.uni-fire {
		width: 750rpx;
		margin-top: 40rpx;

		// 头部
		.header {
			width: 100%;
			position: relative;

			.header-left {
				display: flex;
				padding-top: 28rpx;

				image {
					height: 48rpx;
					width: 48rpx;
					margin-left: 20rpx;
				}

				.header-left-text {
					height: 46rpx;
					font-size: 40rpx;
					font-weight: bold;
					margin-left: 9rpx;
				}
			}

			.header-right {
				position: absolute;
				display: flex;
				float: right;
				right: 0;
				top: 38rpx;

				.header-right-text {
					font-size: 24rpx;
					margin-right: 11rpx;
				}

				image {
					width: 28rpx;
					height: 28rpx;
					margin-right: 20rpx;
				}
			}
		}
	}
	
	// 优惠discount
	.discount {
		height: 228rpx;
		width: 100%;
		margin-top: 16rpx;
		display: flex;
		justify-content: space-between;
		.group-buying {
			display: flex;
			image {
				height: 164rpx;
				width: 164rpx;
				left: 192rpx;
				margin-top: 32rpx;
			}
		}
		.coupon {
			display: flex;
			image {
				width: 140rpx;
				height: 140rpx;
				margin-top: 44rpx;
				margin-right: 32rpx;
			}
		}
	}
	
	// 推荐商品
	.recommend {
		margin-left: 20rpx;
		margin-right: 20rpx;
	}
	
	// 
	.bottom {
		text-align: center;
		margin-top: 38rpx;
		color: #B3C1C4;
		font-size: 24rpx;
	}
</style>
