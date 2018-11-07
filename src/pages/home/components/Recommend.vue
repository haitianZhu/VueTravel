<template>
  <div>
    <div class="title">热销推荐</div>
    <ul>
      <li class="item border-bottom" v-for="item of recommendList" :key="item.id">
        <img
          class="item-img" :src="item.imgUrl"/>
        <div class="item-info">
          <p class="item-title">{{item.title}}</p>
          <p class="item-desc">{{item.desc}}</p>
          <button class="item-button">查看详情</button>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'Recommend',
  data () {
    return {
      recommendList: [{
        id: '0001',
        imgUrl: 'http://img1.qunarzz.com/sight/p0/1412/89/66dadfb4d982e6f88abad45a3e062342.water.jpg_200x200_0443bc40.jpg',
        title: '曲江海洋极地公园',
        desc: 'AAAA景区'
      }, {
        id: '0002',
        imgUrl: 'http://img1.qunarzz.com/sight/p0/1412/89/66dadfb4d982e6f88abad45a3e062342.water.jpg_200x200_0443bc40.jpg',
        title: '曲江海洋极地公园',
        desc: 'AAAA景区'
      }, {
        id: '0003',
        imgUrl: 'http://img1.qunarzz.com/sight/p0/1412/89/66dadfb4d982e6f88abad45a3e062342.water.jpg_200x200_0443bc40.jpg',
        title: '曲江海洋极地公园',
        desc: 'AAAA景区'
      }]
    }
  }
}
</script>

<style lang="stylus" scoped>
  @import "~@/assets/styles/mixins.styl"
  .title
    line-height .8rem
    background #eee
    text-indent .2rem
  .item
    overflow hidden
    display flex
    height 1.9rem
    .item-img
      width 1.7rem
      height 1.7rem
      padding .1rem
    .item-info
      flex 1
      padding .1rem
      width 0
      .item-title
        line-height .54rem
        font-size .32rem
        ellipsis()
      .item-desc
        line-height .4rem
        color #ccc
        ellipsis()
      .item-button
        line-height .44rem
        background #ff9300
        border-radius 0.06rem
        margin-top 0.16rem
        padding 0 .2rem
        color #fff
</style>
