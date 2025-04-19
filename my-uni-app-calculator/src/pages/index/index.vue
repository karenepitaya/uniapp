<template>
  <view class="calculator">
    <view class="title">Classic Calculator</view>
    <view class="display">
      <text class="result">{{ displayValue }}</text>
    </view>
    <view class="keypad">
      <view class="row">
        <button class="key operator" @click="square">X2</button>
        <button class="key operator" @click="appendOperator('/')">&divide;</button>
        <button class="key operator" @click="appendOperator('*')">&times;</button>
        <button class="key" @click="clearDisplay">C</button>
      </view>
      <view class="row">
        <button class="key number" @click="appendNumber('7')">7</button>
        <button class="key number" @click="appendNumber('8')">8</button>
        <button class="key number" @click="appendNumber('9')">9</button>
        <button class="key operator" @click="appendOperator('+')">+</button>
      </view>
      <view class="row">
        <button class="key number" @click="appendNumber('4')">4</button>
        <button class="key number" @click="appendNumber('5')">5</button>
        <button class="key number" @click="appendNumber('6')">6</button>
        <button class="key operator" @click="appendOperator('-')">-</button>
      </view>
      <view class="row last-rows">
        <view class="left-part">
          <view class="row">
            <button class="key number" @click="appendNumber('1')">1</button>
            <button class="key number" @click="appendNumber('2')">2</button>
            <button class="key number" @click="appendNumber('3')">3</button>
          </view>
          <view class="row">
            <button class="key number zero" @click="appendNumber('0')">0</button>
            <button class="key" @click="appendDecimal">.</button>
          </view>
        </view>
        <button class="key operator equal" @click="calculate">=</button>
      </view>
    </view>
  </view>
</template>

<script>
export default {
  data() {
    return {
      displayValue: '0',
      previousValue: null,
      operator: null,
      newNumber: true
    }
  },
  methods: {
    appendNumber(number) {
      if (this.newNumber) {
        this.displayValue = number;
        this.newNumber = false;
      } else {
        this.displayValue = this.displayValue === '0' ? number : this.displayValue + number;
      }
    },
    appendDecimal() {
      if (!this.displayValue.includes('.')) {
        this.displayValue += '.';
      }
    },
    appendOperator(op) {
      this.calculate();
      this.previousValue = parseFloat(this.displayValue);
      this.operator = op;
      this.newNumber = true;
    },
    clearDisplay() {
      this.displayValue = '0';
      this.previousValue = null;
      this.operator = null;
      this.newNumber = true;
    },
    square() {
      const current = parseFloat(this.displayValue);
      this.displayValue = (current * current).toString();
      this.newNumber = true;
    },
    calculate() {
      if (this.previousValue === null || this.operator === null) return;
      
      const current = parseFloat(this.displayValue);
      let result;
      
      switch (this.operator) {
        case '+':
          result = this.previousValue + current;
          break;
        case '-':
          result = this.previousValue - current;
          break;
        case '*':
          result = this.previousValue * current;
          break;
        case '/':
          result = current !== 0 ? this.previousValue / current : 'Error';
          break;
      }
      
      this.displayValue = result.toString();
      this.previousValue = null;
      this.operator = null;
      this.newNumber = true;
    }
  }
}
</script>

<style>
.calculator {
  width: 90%;
  max-width: 650rpx;
  margin: 20rpx auto;
  background-color: #d4d4d4;
  border-radius: 20rpx;
  padding: 20rpx;
  box-shadow: 0 0 20rpx rgba(0, 0, 0, 0.3);
}

.title {
  text-align: center;
  font-size: 40rpx;
  font-weight: bold;
  color: #333;
  margin-bottom: 20rpx;
  font-family: monospace;
}

.display {
  background-color: #e8e8e8;
  padding: 30rpx;
  margin-bottom: 20rpx;
  border-radius: 10rpx;
  border: 2rpx solid #999;
  box-shadow: inset 0 2rpx 5rpx rgba(0, 0, 0, 0.1);
}

.result {
  font-size: 50rpx;
  text-align: right;
  font-family: monospace;
  color: #333;
  display: block;
  min-height: 60rpx;
}

.keypad {
  display: flex;
  flex-direction: column;
  gap: 15rpx;
}

.row {
  display: flex;
  gap: 15rpx;
}

.key {
  flex: 1;
  height: 100rpx;
  font-size: 36rpx;
  background-color: #f0f0f0;
  border: 2rpx solid #999;
  border-radius: 10rpx;
  display: flex;
  align-items: center;
  justify-content: center;
  box-shadow: 0 4rpx 8rpx rgba(0, 0, 0, 0.1);
  transition: all 0.1s ease;
}

.last-rows {
  display: flex;
  gap: 15rpx;
}

.left-part {
  flex: 7;
  display: flex;
  flex-direction: column;
  gap: 15rpx;
}

.zero {
  width: calc((100% - 30rpx) / 3 * 2 + 15rpx);
  flex: none;
}

.equal {
  width: calc((100% - 45rpx) / 4);
  height: 215rpx !important;
  flex: none;
}

.operator {
  background-color: #e0e0e0;
  font-weight: bold;
}

.number {
  background-color: #ffffff;
}

.key:active {
  background-color: #e0e0e0;
  transform: translateY(2rpx);
  box-shadow: 0 2rpx 4rpx rgba(0, 0, 0, 0.1);
}
</style>
