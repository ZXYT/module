<template>
  <div class="container">
    <div>
      <Logo />
      <button @click="showDialog = true">
        showDialog
      </button>
      <Dialog v-if="showDialog" :content="content" @hide="showDialog = false" />
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      showDialog: false,
      content: '我是正文内容'
    }
  }
}
</script>

<style>
</style>
