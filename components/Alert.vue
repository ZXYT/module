<template>
  <div id="tips">
    <i class="iconfont icon-tips" />
    {{ tips }}
  </div>
</template>

<script>
export default {
  props: {
    tips: {
      type: String,
      required: true
    }
  }
}
</script>

<style lang="scss" scoped>
#tips {
  position: fixed;
  top: 10vh;
  left: 50%;
  transform: translateX(-50%);
  width: 200px;
  padding: 15px;
  border-radius: 5px;
  box-shadow: 0 3px 6px rgba(0, 0, 0, 0.16);
  background-color: #eff;
  color: #999;
}
</style>
