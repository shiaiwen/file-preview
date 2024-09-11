<template>
  <view class="img-list">
    <scroll-view
      ref="scrollView"
      class="scroll-view_H"
      scroll-x="true"
      :scroll-into-view="'tab' + tabId"
      scroll-with-animation
      :scroll-left="300"
      show-scrollbar
      @scroll="scroll"
    >
      <view
        v-for="(item, index) in imgList"
        :id="'tab' + tabId"
        :key="index"
        class="scroll-view-item_H"
      >
        <view class="img-container">
          <image
            :class="{ active: index === current }"
            class="img-item"
            mode="aspectFill"
            :src="item"
            @click="handleClick(index)"
          >
          </image>
          <!-- 图片蒙版 -->
          <view
            v-if="index !== current"
            class="mask"
          ></view>
        </view>
      </view>
    </scroll-view>
  </view>
</template>

<script>
export default {
  props: {
    current: {
      type: Number,
      default: 0,
    },
    imgList: {
      type: Array,
      default: () => [],
    },
  },
  data() {
    return {
      tabId: '',
      scrollView: null,
      old: {
        scrollTop: 0,
      },
    };
  },
  mounted() {
    this.test();
  },
  methods: {
    scroll(e) {
      console.log(e);
      this.old.scrollTop = e.detail.scrollTop;
    },
    handleClick(index) {
      this.$emit('change', index);
      this.tabId = this.imgList[index];
    },
    test() {
      this.scrollView = this.$refs.scrollView;
      setTimeout(() => {
        console.log('滚动触发');
        this.tabId = this.imgList[3];
        console.log(this.scrollView, '获取滚动元素');
        this.scrollView.scrollIntoView(`tab${this.tabId}`, 300); // 300 是滚动动画的时长
      }, 3000);
    },
  },
};
</script>

<style lang="scss">
.scroll-view_H {
  white-space: nowrap;
  padding: 0 20rpx;
  width: 100%;
}

.scroll-view-item_H {
  display: inline-block;
  width: 30%;
  height: 150rpx;
  background-color: #fff;
  border-radius: 8rpx;
  text-align: center;
  font-size: 36rpx;
  margin: 0 20rpx;
}

.img-container {
  position: relative;
  height: 150rpx;
  .img-item {
    border-radius: 8rpx;
    border: 2rpx solid #fff;
    width: 200rpx;
    height: 150rpx;
    &.active {
      border: 4rpx solid #fff;
    }
  }
  .mask {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 0, 0.5); /* 调整透明度来控制蒙版的不透明度 */
    pointer-events: none; /* 确保蒙版不会阻止图片的点击事件 */
  }
}
</style>
