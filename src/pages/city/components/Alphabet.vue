<template>
  <ul class="list">
    <li
      class="item"
      v-for="item of letters"
      :key="item"
      @click="clickLetter"
      @touchstart="handleTouchStart"
      @touchend="handleTouchEnd"
      @touchmove="handleTouchMove"
      :ref="item"
    >{{item}}</li>
  </ul>
</template>

<script>
export default {
  name: 'CityAlphabet',
  props: {
    cities: Object
  },
  data () {
    return {
      touchStatus: false,
      startY: 0,
      timer: null
    }
  },
  computed: {
    letters () {
      const letters = []
      for (let i in this.cities) {
        letters.push(i)
      }
      return letters
    }
  },
  updated () {
    this.startY = this.$refs['A'][0].offsetTop
  },
  methods: {
    clickLetter (e) {
      this.$emit('letterClick', e.target.innerHTML)
    },
    handleTouchStart () {
      this.touchStatus = true
    },
    handleTouchEnd () {
      this.touchStatus = false
    },
    handleTouchMove (e) {
      if (this.touchStatus) {
        if (this.timer) {
          clearTimeout(this.timer)
        }
        setTimeout(() => {
          const touchY = e.touches[0].clientY - 80
          const index = Math.floor((touchY - this.startY) / this.$refs['A'][0].clientHeight)
          this.$emit('letterClick', this.letters[index])
        }, 16)
      }
    }
  }
}
</script>

<style lang="stylus" scoped>
  @import "~@/assets/styles/varibles.styl"
  .list
    display flex
    flex-direction column
    justify-content center
    position absolute
    width .4rem
    top 1.58rem
    right 0
    bottom 0
    .item
      line-height .44rem
      text-align center
      color $bgColor
</style>
