<template>
  <div class="header">
    城市选择
    <router-link to="/">
      <div class="iconfont header-back">&#xe624;</div>
    </router-link>
  </div>
</template>

<script>
export default {
  name: 'CityHeader'
}
</script>

<style lang="stylus" scoped>
  @import "~@/assets/styles/varibles.styl"
  .header
    position relative
    overflow hidden
    height $headerHeight
    line-height $headerHeight
    font-size .32rem
    background $bgColor
    color #fff
    text-align center
    .header-back
      position absolute
      width .64rem
      text-align center
      font-size .3rem
      top 0
      left 0
      color #fff
</style>
