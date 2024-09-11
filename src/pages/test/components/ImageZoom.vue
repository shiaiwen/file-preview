<template>
  <view class="imagecontent">
    <movable-area scale-area>
      <movable-view
        direction="all"
        scale
        scale-min="1"
        scale-max="5"
      >
        <image
          :src="currentImg"
          mode="widthFix"
          style="width: 100%; height: 100%"
          @touchstart="touchStart"
          @touchend="touchEnd"
        ></image>
      </movable-view>
    </movable-area>
  </view>
</template>

<script>
export default {
  props: {
    currentImg: {
      type: String,
      default: '',
    },
  },
  data() {
    return {
      startX: 0,
      isDoubleTouch: false, // 用于标记是否是双指触摸
    };
  },
  methods: {
    // 触摸开始事件
    touchStart(event) {
      this.startX = event.touches[0].clientX; // 记录触摸开始时的横坐标
      // 检查触摸点的数量
      if (event.touches.length === 1) {
        console.log('单指触摸');
        this.isDoubleTouch = false;
      } else if (event.touches.length === 2) {
        console.log('双指触摸');
        this.isDoubleTouch = true;
      }
    },
    // 触摸结束事件
    touchEnd(event) {
      if (this.isDoubleTouch) {
        return;
      }
      const endX = event.changedTouches[0].clientX; // 触摸结束时的横坐标
      if (this.startX > endX) {
        this.$emit('left', event);
      } else if (this.startX < endX) {
        this.$emit('right', event);
      }
    },

  },
};
</script>

<style>

movable-area {
  box-sizing: border-box;
  height: 100vh;
  width: 750rpx;
  overflow: hidden;
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
}

movable-view {
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
  height: 100vh;
  width: 750rpx;
}

</style>
