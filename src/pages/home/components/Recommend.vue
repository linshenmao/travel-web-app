<template>
  <div class="recommend">
    <div class="title">热销推荐</div>
    <router-link class="item border-bottom" v-for="item of list" :key='item.id' :to="'/detail/'+item.id">
        <img class="item-img" :src="item.imgUrl">
        <div class="item-info">
          <div class="item-title">{{ item.title }}</div>
          <div class="item-desc">{{ item.desc }}</div>
          <button class="item-btn">查看详情</button>
        </div>
    </router-link>
  </div>
</template>

<script>
export default {
  name: 'Recommend',
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
        display flex
        padding .1rem
        .item-img
            width 2rem
            height 2rem
            padding .1rem
        .item-info
            flex 1
            padding .1rem
            margin 0 .1rem
            min-width 0
            .item-title
                line-height .5rem
                font-size .32rem
                ellipsis()
            .item-desc
                color #777
                line-height .4rem
                font-size .24rem
                ellipsis()
            .item-btn
                color #fff
                background orange
                padding 0 .2rem
                margin .2rem 0
                border-radius .2rem
                line-height .4rem
</style>
