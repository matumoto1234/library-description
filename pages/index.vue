<template>
  <div>
    <transition class="loading">
      <div v-if="isLoading" class="text-center">
        <h1>HelloWorld</h1>
      </div>
    </transition>

    <transition class="content">
      <div v-if="!isLoadingLater" class="text-center">
        <v-btn
          dark
          color="blue"
          min-height="100"
          min-width="100"
          class="mx-2"
          fab
          href="https://twitter.com/matumoto_1234"
        >
          <v-icon dark size="70">
            mdi-twitter
          </v-icon>
        </v-btn>
        <v-btn
          dark
          min-height="100"
          min-width="100"
          fab
          href="https://github.com/matumoto1234/library"
        >
          <v-icon dark size="70">
            mdi-github
          </v-icon>
        </v-btn>

        <v-divider />

        <v-card class="gothic-font">
          コピペなどは自由です。
          <br>
          バグっていることもあるので信用しきらないでください。
          <br>
          バグを見つけたらTwitterなどで教えてくださるとありがたいです。
        </v-card>

        <transition>
          <div v-show="animationFlgs[0]">
            <article>
              <Lottie :options="hamster" />
            </article>
          </div>
        </transition>

        <transition>
          <div v-show="animationFlgs[1]">
            <article>
              <Lottie :options="gear" />
            </article>
          </div>
        </transition>

        <transition>
          <div v-show="animationFlgs[2]">
            <article>
              <Lottie :options="hotspring" />
            </article>
          </div>
        </transition>

        <transition>
          <div v-show="animationFlgs[3]">
            <article>
              <Lottie :options="paperPlane" />
            </article>
          </div>
        </transition>

        <transition>
          <div v-show="animationFlgs[4]">
            <article>
              <Lottie :options="rocket" />
            </article>
          </div>
        </transition>

        <transition>
          <div v-show="animationFlgs[5]">
            <article>
              <Lottie :options="run" />
            </article>
          </div>
        </transition>

        <transition>
          <div v-show="animationFlgs[6]">
            <article>
              <Lottie :options="shapes" />
            </article>
          </div>
        </transition>
      </div>
    </transition>
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
      hamster: {
        animationData: require('~/assets/animation/hamster.json')
      },
      gear: {
        animationData: require('~/assets/animation/gear.json')
      },
      hotspring: {
        animationData: require('~/assets/animation/hotspring.json')
      },
      paperPlane: {
        animationData: require('~/assets/animation/paperPlane.json')
      },
      rocket: {
        animationData: require('~/assets/animation/rocket.json')
      },
      run: {
        animationData: require('~/assets/animation/run.json')
      },
      shapes: {
        animationData: require('~/assets/animation/shapes.json')
      }
    }
  },
  data () {
    return {
      isLoading: true,
      isLoadingLater: true,
      animationFlgs: [
        true,
        false,
        false,
        false,
        false,
        false,
        false
      ],
      showIdx: 0
    }
  },
  mounted () {
    setTimeout(function () {
      this.isLoading = false
      setTimeout(function () {
        this.isLoadingLater = false
      }.bind(this), 500)
    }.bind(this), 750)

    setInterval(function () {
      this.$set(this.animationFlgs, this.showIdx, false)
      this.showIdx = this.getRandomInt(this.animationFlgs.length)
      setTimeout(function () {
        this.$set(this.animationFlgs, this.showIdx, true)
      }.bind(this), 500)
    }.bind(this), 10000)
  },
  methods: {
    getRandomInt (max) {
      return Math.floor(Math.random() * max)
    }
  }
}

</script>

<style scoped>
h1 {
  position: relative;
  padding: 0.25em 1em;
  border-top: solid 2px black;
  border-bottom: solid 2px black;
}
h1:before, h1:after {
  content: '';
  position: absolute;
  top: -7px;
  width: 2px;
  height: -webkit-calc(100% + 14px);
  height: calc(100% + 14px);
  background-color: black;
}
h1:before {
  left: 7px;
}
h1:after {
  right: 7px;
}

/* 以下の v-enter, v-enter-to, v-enter-active がトランジションクラス */
/* 表示アニメーションをする前のスタイル */
.v-enter {
  opacity: 0;
}
/* 表示アニメーション後のスタイル */
.v-enter-to {
  opacity: 1;
}
/* 表示アニメーション動作中のスタイル */
.v-enter-active {
  transition: all 500ms;
}
/* 消去アニメーションをする前のスタイル */
.v-leave {
  opacity: 1;
}
/* 消去アニメーション後のスタイル */
.v-leave-to {
  opacity: 0;
}
/* 消去アニメーション動作中のスタイル */
.v-leave-active {
  transition: all 500ms;
}

.gothic-font {
  font-family: 'LogoTypeGothic';
}
</style>
