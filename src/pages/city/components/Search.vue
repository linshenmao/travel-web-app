<template>
  <div>
    <div class="search">
      <input v-model='keyword' class='search-input' type="text" placeholder="请输入城市名称或拼音">
    </div>
    <div class="search-content" ref="search" v-show="keyword">
      <ul>
        <li class="search-item border-bottom" v-for="item of list"
        :key='item.id' @click="handleCityClick(item.name)">{{item.name}}</li>
        <li v-show="hasList">没有匹配到相关数据</li>
      </ul>
    </div>
  </div>
</template>

<script>
import {mapMutations} from 'vuex'
import Bscroll from 'better-scroll'
export default {
  name: 'Search',
  props: {
    cities: Object
  },
  data () {
    return {
      keyword: '',
      timer: null,
      list: []
    }
  },
  methods: {
    handleCityClick (city) {
      this.changeCity(city)
      this.$router.push('/')
    },
    ...mapMutations(['changeCity'])
  },
  computed: {
    hasList () {
      return !this.list.length
    }
  },
  watch: {
    keyword () {
      if (this.timer) {
        clearTimeout(this.timer)
      }
      if (!this.keyword.length) {
        this.list = []
        return
      }
      this.timer = setTimeout(() => {
        const result = []
        for (let i in this.cities) {
          this.cities[i].forEach(value => {
            if (value.spell.indexOf(this.keyword) > -1 || value.name.indexOf(this.keyword) > -1) {
              result.push(value)
            }
          })
          this.list = result
        }
      }, 100)
    }
  },
  mounted () {
    this.Bscroll = new Bscroll(this.$refs.search)
  }
}
</script>

<style lang='stylus' scoped>
@import '~styles/varibles.styl';
.search
    height .72rem
    line-height .72rem
    padding .08rem
    background $bgColor
    .search-input
        box-sizing border-box
        height .62rem
        line-height .62rem
        width 100%
        color #666
        text-align center
        border-radius .06rem
        padding 0 .1rem
.search-content
    overflow hidden
    background #eee
    position absolute
    top 1.75rem
    left 0
    right 0
    bottom 0
    z-index 9
    line-height .7rem
    .search-item
      padding-left .2rem
      background #fff
</style>
