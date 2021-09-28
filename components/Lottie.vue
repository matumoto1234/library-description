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
  asyncData () {
    return {
      animations: [
        'gear.json',
        'hamster.json',
        'hotspring.json',
        'paperPlane.json',
        'rocket.json',
        'run.json',
        'shapes.json'
      ]
    }
  },
  mounted () {
    const animationEvt = (animation) => {
      lottie.loadAnimation({
        container: this.$refs.animationContainer,
        renderer: 'svg',
        loop: true,
        autoplay: true,
        animationData: animation
      })
    }
    const AnimStorage = () => {
      if (sessionStorage.getItem('access')) {
        // 初回アクセス以外の処理
        animationEvt(this.options.animationData)
      } else {
        // 初回アクセス時の処理
        animationEvt(this.options.animationData)
        sessionStorage.setItem('access', 0)
      }
    }
    AnimStorage()
  },
  methods: {
    getRandomInt (max) {
      return Math.floor(Math.random() * max)
    },
    getRandomAnimation () {
      return this.animations[this.getRandomInt(this.animations.length)]
    }
  }
}
</script>
