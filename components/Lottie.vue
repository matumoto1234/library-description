<template>
  <!-- .animationItem(ref="animationContainer") -->
  <div ref="animationContainer" class="animationItem" />
</template>

<script>
import lottie from 'lottie-web'
export default {
  props: {
    options: {
      type: Object,
      required: true
    }
  },
  mounted () {
    const animationEvt = () => {
      lottie.loadAnimation({
        container: this.$refs.animationContainer,
        renderer: 'svg',
        loop: true,
        autoplay: true,
        animationData: this.options.animationData
      })
    }
    const AnimStorage = () => {
      if (sessionStorage.getItem('access')) {
        // 初回アクセス以外の処理
        animationEvt()
      } else {
        // 初回アクセス時の処理
        animationEvt()
        sessionStorage.setItem('access', 0)
      }
    }
    AnimStorage()
  }
}
</script>
