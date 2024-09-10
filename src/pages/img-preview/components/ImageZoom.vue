<template>
  <view class="imagecontent">
    <movable-area scale-area>
      <movable-view
        direction="all"
        scale
        scale-min="1"
        scale-max="4"
        :scale-value="scale"
        @change="onChange"
        @scale="onScale"
      >
        <image
          :src="imageSrc"
          mode="widthFix"
          style="width: 100%; height: 100%"
        ></image>
      </movable-view>
    </movable-area>
  </view>
</template>

<script>
export default {
  data () {
    return {
      // src: '', // 图片路径
      imageSrc:
        'https://pic.netbian.com/uploads/allimg/240528/213609-17169033698cd1.jpg'
    }
  },
  methods: {
    onChange (e) {
      console.log(e.detail)
    },

    onScale (e) {
      console.log(e.detail)
    }
  }
}
</script>

<style>
.imagecontent {
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
}

movable-view {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 800rpx;
  width: 750rpx;
  color: #fff;
}

movable-area {
  box-sizing: border-box;
  height: 800rpx;
  width: 750rpx;
  /* margin: 50rpx; */
  /* background-color: #ccc; */
  overflow: hidden;
}
</style>
