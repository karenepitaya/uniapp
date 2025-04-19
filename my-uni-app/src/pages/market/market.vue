<template>
  <view class="container">
    <!-- 头部轮播图 -->
    <swiper class="banner" circular :indicator-dots="true" :autoplay="true" :interval="3000" :duration="1000">
      <swiper-item v-for="(item, index) in bannerList" :key="index">
        <image :src="item.image" mode="aspectFill" class="banner-image"></image>
      </swiper-item>
    </swiper>

    <!-- 筛选栏 -->
    <view class="filter-container">
      <view class="filter-item" v-for="(item, index) in filterList" :key="index" @click="selectFilter(index)">
        <text :class="['filter-text', currentFilter === index ? 'active' : '']">{{ item }}</text>
      </view>
    </view>

    <!-- 商品列表 -->
    <view class="goods-list">
      <view class="goods-item" v-for="(item, index) in goodsList" :key="index">
        <image :src="item.image" mode="aspectFill" class="goods-image"></image>
        <view class="goods-info">
          <text class="goods-name">{{ item.name }}</text>
          <text class="goods-price">¥{{ item.price }}</text>
          <text class="goods-sales">已售{{ item.sales }}单</text>
        </view>
      </view>
    </view>
  </view>
</template>

<script>
export default {
  data() {
    return {
      bannerList: [
        { image: '/static/images/banner/market-banner1.jpg' },
        { image: '/static/images/banner/market-banner2.jpg' },
        { image: '/static/images/banner/market-banner3.jpg' }
      ],
      filterList: ['全部', '热门', '新上架', '价格', '销量'],
      currentFilter: 0,
      goodsList: [
        {
          name: '王者荣耀陪玩',
          price: 30,
          sales: 1000,
          image: '/static/images/goods/goods1.jpg'
        },
        {
          name: '和平精英陪玩',
          price: 25,
          sales: 800,
          image: '/static/images/goods/goods2.jpg'
        }
      ]
    }
  },
  methods: {
    selectFilter(index) {
      this.currentFilter = index
      // 后续添加筛选逻辑
    }
  }
}
</script>

<style>
.container {
  padding-bottom: 100rpx;
}

.banner {
  width: 100%;
  height: 300rpx;
}

.banner-image {
  width: 100%;
  height: 100%;
}

.filter-container {
  display: flex;
  padding: 20rpx;
  background-color: #fff;
  border-bottom: 1rpx solid #eee;
}

.filter-item {
  flex: 1;
  text-align: center;
}

.filter-text {
  font-size: 28rpx;
  color: #333;
  padding: 10rpx 0;
}

.filter-text.active {
  color: #007AFF;
  border-bottom: 2rpx solid #007AFF;
}

.goods-list {
  padding: 20rpx;
}

.goods-item {
  display: flex;
  background-color: #fff;
  padding: 20rpx;
  margin-bottom: 20rpx;
  border-radius: 10rpx;
}

.goods-image {
  width: 200rpx;
  height: 200rpx;
  border-radius: 10rpx;
  margin-right: 20rpx;
}

.goods-info {
  flex: 1;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

.goods-name {
  font-size: 28rpx;
  color: #333;
}

.goods-price {
  font-size: 32rpx;
  color: #ff5500;
  font-weight: bold;
}

.goods-sales {
  font-size: 24rpx;
  color: #999;
}
</style> 