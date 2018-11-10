<template>
  <div class="header">
    城市选择
    <router-link to="/">
      <div class="iconfont header-back">&#xe624;</div>
    </router-link>
  </div>
</template>

<script>
export default {
  name: 'CityHeader'
}
</script>

<style lang="stylus" scoped>
  .header
    height: .88rem
    line-height: .88rem
    background: #00bcd4
    font-size: .32rem
    color: #ffffff
    text-align: center
    position :relative
    .header-back
      position: absolute
      top:0
      left:0
      width: .64rem
      text-align: center
      color: #ffffff
      font-size: .4rem
</style>
