<template>
  <div>
    <Lottie :options="lottieOptions" />
  </div>
</template>

<script>
import Lottie from '~/components/Lottie.vue'

export default {
  components: {
    Lottie
  },
  asyncData () {
    return {
      lottieOptions: {
        animationData: require('~/assets/animation/404.json')
      }
    }
  }
}
</script>
