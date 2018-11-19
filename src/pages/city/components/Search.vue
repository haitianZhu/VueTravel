<template>
  <div>
    <div class="search">
      <input class="search-input" type="text" placeholder="输入城市名或拼音" v-model="keyword"/>
    </div>
    <div class="search-content" ref="search" v-show="keyword">
      <ul>
        <li class="search-item border-bottom" v-for="item of list" :key="item.id" @click="handleClick(item.name)">
          {{item.name}}
        </li>
        <li class="search-item border-bottom" v-show="hasNoData">
          没有匹配城市
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import BScroll from 'better-scroll'
import { mapActions } from 'vuex'
export default {
  name: 'CitySearch',
  props: {
    cities: Object
  },
  data () {
    return {
      keyword: '',
      list: [],
      timer: null
    }
  },
  mounted () {
    this.scroll = new BScroll(this.$refs.search)
  },
  computed: {
    hasNoData () {
      return !this.list.length
    }
  },
  methods: {
    handleClick (city) {
      this.changeCity(city)
      this.$router.push('/')
    },
    ...mapActions(['changeCity'])
  },
  watch: {
    keyword () {
      if (this.timer) {
        clearTimeout(this.timer)
      }
      if (!this.keyword) {
        this.list = []
        return
      }
      this.timer = setTimeout(() => {
        const result = []
        for (let i in this.cities) {
          this.cities[i].forEach((value) => {
            if (value.spell.indexOf(this.keyword) > -1 || value.name.indexOf(this.keyword) > -1) {
              result.push(value)
            }
          })
        }
        this.list = result
      }, 100)
    }
  }
}
</script>

<style lang="stylus" scoped>
  @import "~@/assets/styles/varibles.styl"
  .search
    background $bgColor
    height .72rem
    padding 0 0.1rem
    .search-input
      box-sizing border-box
      width 100%
      height .62rem
      line-height .62rem
      text-align center
      border-radius 0.06rem
      color #666
      padding 0 0.1rem
  .search-content
    position: absolute
    overflow hidden
    top 1.58rem
    left 0
    right 0
    bottom 0
    background #eee
    z-index 1
    .search-item
      line-height .62rem
      padding-left 0.2rem
      color #666
      background #fff
</style>
