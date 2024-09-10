<template>
  <view class="img-list">
    <scroll-view
      class="scroll-view_H"
      scroll-x="true"
      @scroll="scroll"
    >
      <view
        id="demo1"
        class="scroll-view-item_H"
      >
        <view class="img-container">
          <image
            class="img active"
            :src="imageSrc"
            mode="widthFix"
            style="width: 100%"
          >
          </image>
          <!-- <view class="mask"></view> -->
        </view>
      </view>
      <view
        id="demo1"
        class="scroll-view-item_H"
      >
        <view class="img-container">
          <image
            class="img active"
            :src="imageSrc"
            mode="widthFix"
            style="width: 100%"
          >
          </image>
          <view class="mask"></view>
        </view>
      </view>
      <view
        id="demo1"
        class="scroll-view-item_H"
      >
        <view class="img-container">
          <image
            class="img active"
            :src="imageSrc"
            mode="widthFix"
            style="width: 100%"
          >
          </image>
          <view class="mask"></view>
        </view>
      </view>
      <view
        id="demo1"
        class="scroll-view-item_H"
      >
        <view class="img-container">
          <image
            class="img active"
            :src="imageSrc"
            mode="widthFix"
            style="width: 100%"
          >
          </image>
          <view class="mask"></view>
        </view>
      </view>
      <view
        id="demo1"
        class="scroll-view-item_H"
      >
        <view class="img-container">
          <image
            class="img active"
            :src="imageSrc"
            mode="widthFix"
            style="width: 100%"
          >
          </image>
          <view class="mask"></view>
        </view>
      </view>
      <view
        id="demo1"
        class="scroll-view-item_H"
      >
        <view class="img-container">
          <image
            class="img active"
            :src="imageSrc"
            mode="widthFix"
            style="width: 100%"
          >
          </image>
          <view class="mask"></view>
        </view>
      </view>
    </scroll-view>
  </view>
</template>

<script>
export default {
  data() {
    return {
      // src: '', // 图片路径
      imageSrc:
        'https://pic.netbian.com/uploads/allimg/240528/213609-17169033698cd1.jpg',
      old: {
        scrollTop: 0,
      },
    };
  },
  methods: {
    scroll(e) {
      console.log(e);
      this.old.scrollTop = e.detail.scrollTop;
    },
  },
};
</script>

<style lang="scss">
.scroll-view_H {
  white-space: nowrap;
  padding: 0 40rpx;
  /* width: 100%; */
  width: 100%;
}

.scroll-view-item_H {
  display: inline-block;
  width: 30%;
  /* width: 100%; */
  height: 90rpx;
  line-height: 90rpx;
  background-color: #fff;
  border-radius: 8rpx;
  text-align: center;
  font-size: 36rpx;
  margin: 0 20rpx;
}

.img-container {
  position: relative;
  .img {
    border-radius: 8rpx;
    border: 2rpx solid #fff;
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
