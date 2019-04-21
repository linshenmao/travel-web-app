<template>
  <div class="header">
    城市列表
    <router-link to='/'>
      <div class="iconfont header-back">&#xe622;</div>
    </router-link>
  </div>
</template>

<script>
export default {
  name: 'CityHeader'
}
</script>

<style lang='stylus' scoped>
@import '~styles/varibles.styl';
.header
    position relative
    overflow hidden
    line-height $headerHeight
    height $headerHeight
    background $bgColor
    color #fff
    text-align center
    font-size .32rem
    .header-back
        position absolute
        top 0
        left 0
        color #fff
        width .64rem
        text-align center
</style>
