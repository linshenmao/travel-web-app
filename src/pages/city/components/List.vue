<template>
  <div class="list" ref='wrapper'>
    <div>
        <div class="area">
        <div class="title border-bottom">当前城市</div>
        <div class="button-list">
            <div class="button-wrapper">
                <div class="button">{{this.currentCity}}</div>
            </div>
        </div>
    </div>
    <div class="area">
        <div class="title border-bottom">热门城市</div>
        <div class="button-list">
            <div class="button-wrapper" v-for="item of hotCities" :key='item.id' @click="handleCityClick(item.name)">
                <div class="button">{{item.name}}</div>
            </div>
        </div>
    </div>
    <div class="area" v-for="(item,key) of cities" :key="key" :ref='key'>
        <div class="title border-bottom">{{key}}</div>
        <div class="item-list" v-for="inneritem of item" :key="inneritem.id" @click="handleCityClick(inneritem.name)">
            <div class="item border-bottom">{{inneritem.name}}</div>
        </div>
    </div>
    </div>
  </div>
</template>

<script>
import BScroll from 'better-scroll'
import {mapState, mapMutations} from 'vuex'
export default {
  name: 'List',
  props: {
    hotCities: Array,
    cities: Object,
    letter: String
  },
  methods: {
    handleCityClick (city) {
      this.changeCity(city)
      this.$router.push('/')
    },
    ...mapMutations(['changeCity'])
  },
  computed: {
    ...mapState({
      currentCity: 'city'
    })
  },
  mounted () {
    this.scroll = new BScroll(this.$refs.wrapper)
  },
  watch: {
    letter () {
      if (this.letter) {
        const element = this.$refs[this.letter][0]
        this.scroll.scrollToElement(element)
      }
    }
  }
}
</script>

<style lang='stylus' scoped>
@import '~styles/varibles.styl';
.list
    position absolute
    top 1.75rem
    left 0
    right 0
    bottom 0
    overflow hidden
    .area
        .title
            line-height .62rem
            padding-left .2rem
            background #eee
        .border-bottom
            &:before
                border-color #ccc
            &:after
                border-color #ccc
        .border-bottom
            &:before
                border-color #ccc
            color #666
        .button-list
            overflow hidden
            padding .1rem .6rem .1rem .1rem
            .button-wrapper
                float left
                width 33.3%
                .button
                    text-align center
                    border .02rem solid #ccc
                    padding .1rem 0
                    margin .1rem
                    border-radius .06rem
        .item-list
            width 100%
            .item
                line-height .8rem
                padding-left .2rem
</style>
