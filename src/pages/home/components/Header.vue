<template>
  <div class="header">
    <div class="header-left">
      <div class="iconfont back-icon">&#xe624;</div>
    </div>
    <div class="header-input">
      <span class="iconfont">&#xe64a;</span>
      输入城市/景点/游玩信息
    </div>
    <div class="header-right">
      城市
      <span class="iconfont arrow_icon">&#xe65c;</span>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Header'
}
</script>

<style lang="stylus" scoped>
  @import "~@/assets/styles/varibles.styl"
  .header
    display flex
    line-height .86rem
    background $bgColor
    color: #fff
    .header-left
      width .64rem
      float left
      .back-icon
        text-align center
        font-size .3rem
    .header-input
      flex 1
      background #fff
      border-radius 0.1rem
      padding-left 0.2rem
      margin-top 0.12rem
      line-height .64rem
      height .64rem
      margin-left 0.2rem
      color #ccc
    .header-right
      width 1.24rem
      float right
      text-align center
      .arrow_icon
        margin-left -0.04rem
</style>
