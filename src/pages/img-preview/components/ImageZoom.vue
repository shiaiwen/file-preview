<template>
  <view class="imagecontent">
    <swiper
      class="swiper"
      circular
      :indicator-dots="indicatorDots"
      :autoplay="autoplay"
      :interval="interval"
      :duration="duration"
      :current="current"
      @change="onSwiperChange"
    >
      <swiper-item v-for="(item, index) in imgList" :key="index">
        <movable-area>
          <movable-view direction="all" scale scale-min="1" scale-max="5">
            <image
              :src="item"
              mode="widthFix"
              style="width: 100%; height: 100%"
            ></image>
          </movable-view>
        </movable-area>
      </swiper-item>
    </swiper>
  </view>
</template>

<script>
import { EventBus } from '@/utils/eventBus';

export default {
  props: {
    imgList: {
      type: Array,
      default: () => [],
    },
  },
  data() {
    return {
      indicatorDots: false,
      autoplay: false,
      interval: 2000,
      duration: 500,
      current: 0,
    };
  },
  mounted() {
    EventBus.$on('current-change', (v) => {
      this.current = v;
    });
  },

  methods: {
    onSwiperChange(event) {
      const current = event.detail.current;
      // 向父组件传递事件
      this.$emit('change', current);
      // 向下面 imgalist 组件传递事件
      EventBus.$emit('change', current);
    },
  },
  beforedestroy() {},
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

.swiper {
  height: 100vh;
}
</style>
