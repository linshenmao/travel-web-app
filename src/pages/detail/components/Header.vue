<template>
  <div>
    <router-link tag='div' to='/' class="header-abs" v-show="showAbs">
      <div class="iconfont header-icon">&#xe622;</div>
    </router-link>
    <div class="header-fixed" v-show="!showAbs" :style="opacityStyle">
      景点详情
      <router-link to='/'>
      <div class="iconfont header-fixed-back">&#xe622;</div>
      </router-link>
    </div>
  </div>
</template>

<script>
export default {
  name: 'gallaryHeader',
  data () {
    return {
      showAbs: true,
      opacityStyle: {
        opacity: 0
      }
    }
  },
  methods: {
    handleShowAbs () {
      const top = document.documentElement.scrollTop
      if (top > 60) {
        this.showAbs = false
        let opacity = top / 140
        opacity = opacity > 1 ? 1 : opacity
        this.opacityStyle = { opacity }
      } else {
        this.showAbs = true
      }
    }
  },
  activated () {
    window.addEventListener('scroll', this.handleShowAbs)
  },
  deactivated () {
    window.removeEventListener('scroll', this.handleShowAbs)
  }
}
</script>

<style lang="stylus" scoped>
@import '~styles/varibles.styl';
  .header-abs
    position absolute
    top .2rem
    left .2rem
    width .8rem
    border-radius .4rem
    text-align center
    line-height .8rem
    height .8rem
    background rgba(0,0,0,.6)
    .header-icon
      color #fff
      font-size .34rem
  .header-fixed
    z-index 2
    position fixed
    top 0
    left 0
    right 0
    line-height $headerHeight
    height $headerHeight
    background $bgColor
    color #fff
    text-align center
    font-size .32rem
    .header-fixed-back
        position absolute
        top 0
        left 0
        color #fff
        width .64rem
        text-align center
</style>
