<template>
  <div>
   <div class="item" v-for="(item, index) of list" :key="index">
    <div class="item-title border-bottom">
      <span class="iconfont item-title-icon">&#xe612;</span>
      {{item.title}}
    </div>
    <div class="item-children" v-if="item.children">
      <detail-list :list='item.children'></detail-list>
    </div>
   </div>
  </div>
</template>

<script>
export default {
  name: 'DetailList',
  props: {
    list: Array
  }
}
</script>

<style lang="stylus" scoped>
  .item-title
    font-size .32rem
    padding 0 .3rem
    height .8rem
    line-height .8rem
    .item-title-icon
      color #09f
      margin-right .1rem
   .item-children
     padding 0 .3rem
</style>
