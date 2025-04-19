<template>
  <view class="container">
    <!-- 头部轮播图 -->
    <swiper class="banner" circular :indicator-dots="true" :autoplay="true" :interval="3000" :duration="1000">
      <swiper-item v-for="(item, index) in bannerList" :key="index">
        <image :src="item.image" mode="aspectFill" class="banner-image"></image>
      </swiper-item>
    </swiper>

    <!-- 接单派单入口 -->
    <view class="entry-container">
      <view class="entry-item" @click="navigateTo('receive')">
        <image src="/static/images/receive.png" mode="aspectFit" class="entry-icon"></image>
        <text>接单</text>
      </view>
      <view class="entry-item" @click="navigateTo('dispatch')">
        <image src="/static/images/dispatch.png" mode="aspectFit" class="entry-icon"></image>
        <text>派单</text>
      </view>
    </view>

    <!-- 活动内容 -->
    <view class="activity-container">
      <view class="activity-title">热门活动</view>
      <view class="activity-list">
        <view class="activity-item" v-for="(item, index) in activityList" :key="index">
          <image :src="item.image" mode="aspectFill" class="activity-image"></image>
          <text class="activity-name">{{ item.name }}</text>
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
        { image: '/static/images/banner/banner1.jpg' },
        { image: '/static/images/banner/banner2.jpg' },
        { image: '/static/images/banner/banner3.jpg' }
      ],
      activityList: [
        { name: '新人专享', image: '/static/images/activity/activity1.jpg' },
        { name: '限时特惠', image: '/static/images/activity/activity2.jpg' },
        { name: '热门游戏', image: '/static/images/activity/activity3.jpg' }
      ]
    }
  },
  methods: {
    navigateTo(type) {
      // 后续添加导航逻辑
      console.log('导航到:', type)
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

.entry-container {
  display: flex;
  justify-content: space-around;
  padding: 30rpx;
  background-color: #fff;
  margin: 20rpx 0;
}

.entry-item {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.entry-icon {
  width: 80rpx;
  height: 80rpx;
  margin-bottom: 10rpx;
}

.activity-container {
  padding: 20rpx;
  background-color: #fff;
}

.activity-title {
  font-size: 32rpx;
  font-weight: bold;
  margin-bottom: 20rpx;
}

.activity-list {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
}

.activity-item {
  width: 48%;
  margin-bottom: 20rpx;
}

.activity-image {
  width: 100%;
  height: 200rpx;
  border-radius: 10rpx;
}

.activity-name {
  font-size: 28rpx;
  margin-top: 10rpx;
  display: block;
}
</style>
