<template>
  <view v-if="visible" class="modal" @touchmove.prevent>
    <view class="content">
      <slot></slot>
    </view>
  </view>
</template>

<script>
export default {
  props: {
    visible: {
      type: Boolean,
      default: false
    }
  },
  methods: {
    hide () {
      this.$emit('update:visible', false)
    }
  }
}
</script>

<style scoped>
.modal {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  background-color: rgba(0, 0, 0, 1);
}

.content {
  background-color: transparent;
  height: 100vh;
}
</style>
