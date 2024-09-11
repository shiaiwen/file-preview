<template>
  <view class="box">
    <scroll-view
      scroll-y
      class="container"
      :scroll-into-view="toView"
    >
      <view
        v-for="(item,index) in items"
        :id="'item'+index"
        :key="index"
        class="item"
      >
        {{ item }}
      </view>
    </scroll-view>
    <button @click="scroll">
      滚动
    </button>
  </view>
</template>

<script>
export default {
  data() {
    return {
      items: [
        /* 你的数据列表 */
        1, 2, 3, 4, 5,
      ],
      index: 0,
      toView: '', // 用于控制滚动到指定元素的 ID
    };
  },
  methods: {
    scroll() {
      this.$nextTick(() => {
        this.toView = `item${this.index}`;
        this.index++;
      });
    },
  },
};
</script>

<style>
.container {
  /* 容器样式 */
  height: 200px;
  overflow-y: scroll;
}
.item {
  height: 100px; /* 根据你的布局调整 */
}
</style>
