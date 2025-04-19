<template>
  <view class="container">
    <!-- 订单类型切换 -->
    <view class="order-type">
      <view class="type-item" :class="{ active: currentType === 'today' }" @click="switchType('today')">
        <text>今日订单</text>
      </view>
      <view class="type-item" :class="{ active: currentType === 'all' }" @click="switchType('all')">
        <text>历史订单</text>
      </view>
    </view>

    <!-- 订单列表 -->
    <view class="order-list">
      <view class="order-item" v-for="(item, index) in orderList" :key="index">
        <view class="order-header">
          <text class="order-time">{{ item.time }}</text>
          <text class="order-status">{{ item.status }}</text>
        </view>
        <view class="order-content">
          <image :src="item.image" mode="aspectFill" class="order-image"></image>
          <view class="order-info">
            <text class="order-name">{{ item.name }}</text>
            <text class="order-price">¥{{ item.price }}</text>
          </view>
        </view>
        <view class="order-footer">
          <button class="btn" v-if="item.status === '待接单'" @click="handleOrder(item, 'accept')">接单</button>
          <button class="btn" v-if="item.status === '进行中'" @click="handleOrder(item, 'complete')">完成</button>
        </view>
      </view>
    </view>
  </view>
</template>

<script>
export default {
  data() {
    return {
      currentType: 'today',
      orderList: [
        {
          time: '2024-04-19 10:00',
          status: '待接单',
          name: '王者荣耀陪玩',
          price: 30,
          image: '/static/images/goods/goods1.jpg'
        },
        {
          time: '2024-04-19 09:30',
          status: '进行中',
          name: '和平精英陪玩',
          price: 25,
          image: '/static/images/goods/goods2.jpg'
        }
      ]
    }
  },
  methods: {
    switchType(type) {
      this.currentType = type
      // 后续添加切换订单类型逻辑
    },
    handleOrder(item, action) {
      // 后续添加订单处理逻辑
      console.log('处理订单:', item, action)
    }
  }
}
</script>

<style>
.container {
  padding-bottom: 100rpx;
}

.order-type {
  display: flex;
  background-color: #fff;
  border-bottom: 1rpx solid #eee;
}

.type-item {
  flex: 1;
  text-align: center;
  padding: 20rpx 0;
}

.type-item.active {
  color: #007AFF;
  border-bottom: 2rpx solid #007AFF;
}

.order-list {
  padding: 20rpx;
}

.order-item {
  background-color: #fff;
  border-radius: 10rpx;
  margin-bottom: 20rpx;
  padding: 20rpx;
}

.order-header {
  display: flex;
  justify-content: space-between;
  margin-bottom: 20rpx;
}

.order-time {
  font-size: 24rpx;
  color: #999;
}

.order-status {
  font-size: 24rpx;
  color: #ff5500;
}

.order-content {
  display: flex;
  margin-bottom: 20rpx;
}

.order-image {
  width: 120rpx;
  height: 120rpx;
  border-radius: 10rpx;
  margin-right: 20rpx;
}

.order-info {
  flex: 1;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

.order-name {
  font-size: 28rpx;
  color: #333;
}

.order-price {
  font-size: 32rpx;
  color: #ff5500;
  font-weight: bold;
}

.order-footer {
  display: flex;
  justify-content: flex-end;
}

.btn {
  margin-left: 20rpx;
  font-size: 28rpx;
  padding: 10rpx 30rpx;
  border-radius: 30rpx;
  background-color: #007AFF;
  color: #fff;
}
</style> 