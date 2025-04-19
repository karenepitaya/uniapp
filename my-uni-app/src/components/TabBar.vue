<template>
  <view class="tab-bar">
    <view class="tab-item" v-for="(item, index) in tabList" :key="index" @click="switchTab(item)">
      <image :src="currentTab === item.key ? item.selectedIcon : item.icon" mode="aspectFit" class="tab-icon"></image>
      <text :class="['tab-text', currentTab === item.key ? 'active' : '']">{{ item.text }}</text>
    </view>
  </view>
</template>

<script>
export default {
  data() {
    return {
      currentTab: 'index',
      tabList: [
        {
          key: 'index',
          text: '首页',
          icon: '/static/images/tabbar/home.png',
          selectedIcon: '/static/images/tabbar/home-active.png'
        },
        {
          key: 'market',
          text: '市场',
          icon: '/static/images/tabbar/market.png',
          selectedIcon: '/static/images/tabbar/market-active.png'
        },
        {
          key: 'orders',
          text: '订单',
          icon: '/static/images/tabbar/orders.png',
          selectedIcon: '/static/images/tabbar/orders-active.png'
        },
        {
          key: 'about',
          text: '我的',
          icon: '/static/images/tabbar/about.png',
          selectedIcon: '/static/images/tabbar/about-active.png'
        }
      ]
    }
  },
  methods: {
    switchTab(item) {
      this.currentTab = item.key
      uni.switchTab({
        url: `/pages/${item.key}/${item.key}`
      })
    }
  }
}
</script>

<style>
.tab-bar {
  position: fixed;
  bottom: 0;
  left: 0;
  right: 0;
  height: 100rpx;
  background-color: #fff;
  display: flex;
  border-top: 1rpx solid #eee;
}

.tab-item {
  flex: 1;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.tab-icon {
  width: 40rpx;
  height: 40rpx;
  margin-bottom: 4rpx;
}

.tab-text {
  font-size: 24rpx;
  color: #999;
}

.tab-text.active {
  color: #007AFF;
}
</style> 