<template>
  <view class="container">
    <button @click="showModal">显示弹框</button>
    <full-screen-black-modal
      :visible="modalVisible"
      @update:visible="modalVisible = $event"
    >
      <!-- 弹框内容 -->
      <view :animation="animationData" class="wrapper">
        <!-- 标题 -->
        <Nav
          class="nav"
          :total="imgList.length"
          :current="current + 1"
          @close="modalVisible = false"
        />
        <!-- 图片缩放组件 -->
        <ImageZoom
          :img-list="imgList"
          class="image-zoom"
          @change="handleChange"
        />
        <!-- 图片缩略图列表组件 -->
        <ImageList
          v-if="imgList.length > 0"
          class="img-list"
          :img-list="imgList"
        />
      </view>
    </full-screen-black-modal>
  </view>
</template>

<script>
import FullScreenBlackModal from './components/FullScreenBlackModal.vue';
import ImageZoom from './components/ImageZoom.vue';
import ImageList from './components/ImageList.vue';
import Nav from './components/Nav.vue';

export default {
  components: {
    FullScreenBlackModal,
    ImageZoom,
    ImageList,
    Nav,
  },
  data() {
    return {
      modalVisible: false, // 遮罩层显示
      animationData: {}, // modal动画对象，
      imgList: [
        'http://www.sxeepoc.com/upload/202107/13/202107131654563484.png',
        'http://www.sxeepoc.com/upload/202107/13/202107131657014437.png',
        'http://www.sxeepoc.com/upload/202107/13/202107131657333191.png',
        'http://www.sxeepoc.com/upload/202107/13/202107131657014437.png',
      ], // 图片数组
      current: 0,
    };
  },
  computed: {},
  methods: {
    showModal() {
      this.modalVisible = true;
      this.createAnimation();
    },
    createAnimation() {
      const animation = uni.createAnimation({
        duration: 300,
        timingFunction: 'ease-in-out',
      });
      animation.opacity(1).scale(1, 1).step();
      this.animationData = animation.export();
    },
    handleChange(index) {
      this.current = index;
    },
  },
};
</script>

<style lang="scss" scoped>
.container {
  padding: 20px;
  width: 100%;
}

.wrapper {
  display: flex;
  justify-content: center;
  flex-direction: column;

  .nav {
    height: 80rpx;
    margin: 20rpx 0;
    width: 100%;
    position: fixed;
    top: 0;
    z-index: 999;
  }

  .image-zoom {
    height: 100vh;
    width: 100%;
  }
  .img-list {
    position: fixed;
    bottom: 100rpx;
    left: 10rpx;
    right: 10rpx;
    width: calc(100% - 20rpx);
    z-index: 999;
  }
}
</style>
