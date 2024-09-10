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
        <Nav class="nav" />
        <!-- 图片缩放组件 -->
        <ImageZoom :src="imageSrc" class="image-zoom" />
        <!-- 图片缩略图列表组件 -->
        <ImageList class="img-list" />
        <!-- 关闭 -->
      </view>
    </full-screen-black-modal>
  </view>
</template>

<script>
import FullScreenBlackModal from './components/FullScreenBlackModal.vue'
import ImageZoom from './components/ImageZoom.vue'
import ImageList from './components/ImageList.vue'
import Nav from './components/Nav.vue'

export default {
  components: {
    FullScreenBlackModal,
    ImageZoom,
    ImageList,
    Nav
  },
  data () {
    return {
      modalVisible: false,
      animationData: {},
      imageSrc:
        'https://pic.netbian.com/uploads/allimg/240528/213609-17169033698cd1.jpg'
    }
  },
  methods: {
    showModal () {
      this.modalVisible = true
      this.createAnimation()
    },
    createAnimation () {
      const animation = uni.createAnimation({
        duration: 300,
        timingFunction: 'ease-in-out'
      })
      animation.opacity(1).scale(1, 1).step()
      this.animationData = animation.export()
    }
  }
}
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
  }

  .image-zoom {
    height: 77vh;
    width: 100%;
  }
}
</style>
