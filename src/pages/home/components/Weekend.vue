<template>
  <div class="recommend">
    <div class="title">周末去哪儿</div>
    <div class="item border-bottom" v-for="item of list" :key='item.id'>
      <div class="item-wrapper">
        <img class="item-img" :src="item.imgUrl">
      </div>
        <div class="item-info">
          <div class="item-title">{{ item.title }}</div>
          <div class="item-desc">{{ item.desc }}</div>
        </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Weekend',
  props: {
    list: Array
  }
}
</script>

<style lang='stylus' scoped>
@import '~styles/mixins.styl';
.recommend
    margin-top .2rem
    .title
        line-height .8rem
        background #eee
        text-indent .4rem
        font-size .32rem
    .item
        overflow hidden
        .item-wrapper
          overflow hidden
          height 0
          padding-bottom 37.6%
          .item-img
            width 100%
        .item-info
            padding .2rem
            margin-right 2rem
            min-width 0
            .item-title
                line-height .4rem
                font-size .26rem
                ellipsis()
            .item-desc
                color #666
                line-height .4rem
                font-size .24rem
                ellipsis()
</style>
