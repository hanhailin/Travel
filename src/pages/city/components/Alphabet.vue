<template>
  <div class="list">
    <li class="item" v-for="(item, key) of cities" :key="key">{{key}}</li>
  </div>
</template>

<script>
export default {
  name: 'CityAlphabet',
  props: {
    cities: Object
  }
}
</script>

<style lang="stylus" scoped>
  @import '~styles/varibles.styl'
  .list
    display: flex
    flex-direction: column
    justify-content: center
    position: absolute
    right: 0
    top: 1.58rem
    bottom: 0
    width: .4rem
    list-style: none
    .item
      text-align: center
      line-height: .44rem
      color: $bgColor
</style>
