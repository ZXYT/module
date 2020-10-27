<template>
  <div id="dialog">
    <transition name="mask">
      <div v-if="showMask" class="mask" />
    </transition>

    <transition>
      <Alert v-if="showAlert" :tips="tips" />
    </transition>

    <transition>
      <Module v-if="showModule" :content="content" @hideModule="hideModule" />
    </transition>
  </div>
</template>

<script>
export default {
  props: {
    content: {
      type: String,
      required: true
    },
    duration: {
      type: Number,
      default: 2000
    }
  },
  data () {
    return {
      tips: '',
      showMask: false,
      showModule: false,
      showAlert: false
    }
  },
  mounted () {
    this.show()
  },
  methods: {
    show () {
      this.showModule = true
      this.showMask = true
    },
    hideModule (type) {
      if (type === 'cancel') {
        this.tips = '您取消了'
        this.$emit('cancel')
      } else if (type === 'confirm') {
        this.tips = '您确定了'
        this.$emit('confirm')
      }
      this.showModule = false
      this.showMask = false
      setTimeout(() => {
        this.auto()
      }, 50)
    },
    auto () {
      this.showAlert = true
      setTimeout(() => {
        this.showAlert = false
        setTimeout(() => {
          this.$emit('hide')
        }, 50)
      }, this.duration)
    }
  }
}
</script>

<style lang="scss" scoped>
#dialog {
  position: fixed;
  top: 0;
  left: 0;
  .mask {
    position: fixed;
    height: 100%;
    width: 100%;
    background-color: rgba(0, 0, 0, 0.5);
  }
}
.mask-enter,
.mask-leave-to {
  opacity: 0;
}
.mask-enter-active,
.mask-leave-active {
  transition: all 0.3s;
}
.mask-enter-to,
.mask-leave {
  opacity: 1;
}

.v-enter,
.v-leave-to {
  opacity: 0;
  transform: translate(-50%, -100%) !important;
}
.v-enter-active,
.v-leave-active {
  transition: all 0.3s;
}
.v-enter-to,
.v-leave {
  opacity: 1;
  transform: translate(-50%, 0) !important;
}
</style>
