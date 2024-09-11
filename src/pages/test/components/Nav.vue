<template>
  <view class="nav-wrapper">
    <view
      class="close"
      hover-class="hover"
      @click="handleClose"
    >
      X
    </view>
    <view class="title">
      {{ current }} / {{ total }}
    </view>
  </view>
</template>

<script>
export default {
  props: {
    current: {
      type: Number,
      default: 0,
    },
    total: {
      type: Number,
      default: 0,
    },
  },
  data() {
    return {};
  },
  methods: {
    handleClose() {
      this.$emit('close');
    },
  },
};
</script>

<style lang="scss" scoped>
.nav-wrapper {
  width: 100%;
  position: relative;
  color: #fff;
  .close {
    position: absolute;
    left: 20rpx;
    height: 80rpx;
    line-height: 80rpx;
    width: 80rpx;
    text-align: center;
    cursor: pointer;
    .hover {
      opacity: 0.8;
    }
  }
  .title {
    text-align: center;
    height: 80rpx;
    line-height: 80rpx;
    color: #fff;
  }
}
</style>
