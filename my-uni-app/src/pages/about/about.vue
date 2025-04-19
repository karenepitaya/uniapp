<template>
  <view class="container">
    <!-- 用户信息卡片 -->
    <view class="user-card">
      <image class="avatar" :src="userInfo.avatar || '/static/images/default-avatar.png'" mode="aspectFill"></image>
      <view class="user-info">
        <text class="nickname">{{ userInfo.nickname || '未登录' }}</text>
        <text class="id">ID: {{ userInfo.id || '--' }}</text>
      </view>
      <button class="login-btn" v-if="!userInfo.id" @click="handleLogin">登录/注册</button>
    </view>

    <!-- 功能列表 -->
    <view class="menu-list">
      <view class="menu-item" v-for="(item, index) in menuList" :key="index" @click="handleMenu(item)">
        <text class="menu-icon">{{ item.icon }}</text>
        <text class="menu-name">{{ item.name }}</text>
        <text class="menu-arrow">></text>
      </view>
    </view>

    <!-- 退出登录 -->
    <view class="logout" v-if="userInfo.id" @click="handleLogout">
      <text>退出登录</text>
    </view>
  </view>
</template>

<script>
export default {
  data() {
    return {
      userInfo: {
        id: '',
        nickname: '',
        avatar: ''
      },
      menuList: [
        { name: '我的钱包', icon: '💰' },
        { name: '我的订单', icon: '📋' },
        { name: '我的收藏', icon: '⭐' },
        { name: '设置', icon: '⚙️' }
      ]
    }
  },
  methods: {
    handleLogin() {
      // 后续添加登录逻辑
      console.log('登录')
    },
    handleLogout() {
      // 后续添加退出登录逻辑
      console.log('退出登录')
    },
    handleMenu(item) {
      // 后续添加菜单点击逻辑
      console.log('点击菜单:', item.name)
    }
  }
}
</script>

<style>
.container {
  padding-bottom: 100rpx;
}

.user-card {
  display: flex;
  align-items: center;
  padding: 40rpx;
  background-color: #fff;
  margin-bottom: 20rpx;
}

.avatar {
  width: 120rpx;
  height: 120rpx;
  border-radius: 60rpx;
  margin-right: 30rpx;
}

.user-info {
  flex: 1;
}

.nickname {
  font-size: 32rpx;
  color: #333;
  margin-bottom: 10rpx;
  display: block;
}

.id {
  font-size: 24rpx;
  color: #999;
}

.login-btn {
  font-size: 28rpx;
  color: #007AFF;
  background-color: transparent;
  padding: 10rpx 30rpx;
  border: 1rpx solid #007AFF;
  border-radius: 30rpx;
}

.menu-list {
  background-color: #fff;
  margin-bottom: 20rpx;
}

.menu-item {
  display: flex;
  align-items: center;
  padding: 30rpx;
  border-bottom: 1rpx solid #eee;
}

.menu-icon {
  font-size: 40rpx;
  margin-right: 20rpx;
}

.menu-name {
  flex: 1;
  font-size: 28rpx;
  color: #333;
}

.menu-arrow {
  font-size: 28rpx;
  color: #999;
}

.logout {
  margin: 40rpx;
  text-align: center;
  padding: 20rpx;
  background-color: #fff;
  border-radius: 10rpx;
  color: #ff5500;
  font-size: 28rpx;
}
</style> 