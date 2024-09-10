<template>
  <view class="nav-wrapper">
    <view class="close"> X </view>
    <view class="title"> 1 / 5 </view>
  </view>
</template>

<script>
export default {
  data () {
    return {}
  },
  methods: {}
}
</script>

<style lang="scss" scoped>
.nav-wrapper {
  width: 100%;
  position: relative;
  color: #fff;
  .close {
    position: absolute;
    left: 30rpx;
    padding: 20rpx;
    cursor: pointer;
  }
  .title {
    text-align: center;
    height: 80rpx;
    line-height: 80rpx;
    color: #fff;
  }
}
</style>
