<template>
  <div id="module">
    <div v-if="title" class="head">
      {{ title }}
    </div>
    <div class="content">
      {{ content }}
    </div>
    <div class="btns">
      <button @click="handleclick('cancel')">
        取消
      </button>
      <button class="primary" @click="handleclick('confirm')">
        确定
      </button>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    title: {
      type: String,
      default: ''
    },
    content: {
      type: String,
      required: true
    }
  },
  methods: {
    handleclick (type) {
      if (type === 'cancel') {
        this.$emit('hideModule', 'cancel')
      } else if (type === 'confirm') {
        this.$emit('hideModule', 'confirm')
      }
    }
  }
}
</script>

<style lang="scss" scoped>
#module {
  position: fixed;
  top: 20vh;
  left: 50%;
  transform: translateX(-50%);
  z-index: 100;
  border-radius: 5px;
  background-color: #fff;
  width: 400px;

  .head {
    padding: 20px;
    font-weight: 700;
    padding-bottom: 20px;
  }

  .content {
    padding: 20px;
  }

  .btns {
    text-align: right;
    padding: 20px;
    button {
      margin-left: 10px;
      padding: 8px 15px;
      border-radius: 5px;
      border: 1px solid #dde;
      background-color: #fff;
      &:hover {
        background-color: #eef;
      }
      &.primary {
        background-color: #49f;
        color: #fff;
        &:hover {
          background-color: #99f;
        }
      }
    }
  }
}
</style>
