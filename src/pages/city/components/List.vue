<template>
  <div class="list" ref="warpper">
    <div>
      <div class="area">
        <div class="title border-topbottom">当前城市</div>
        <div class="button-list">
          <div class="button-warpper">
            <div class="button">{{this.$store.state.city}}</div>
          </div>
        </div>
      </div>
      <div class="area">
        <div class="title border-topbottom">热门城市</div>
        <div class="button-list">
          <div class="button-warpper" v-for="item of hot" :key="item.id" @click="handleClickCity(item.name)">
            <div class="button">{{item.name}}</div>
          </div>
        </div>
      </div>
      <div
        class="area"
        v-for="(item, key) of cities"
        :key="key"
        :ref="key"
      >
        <div class="title border-topbottom">{{key}}</div>
        <div class="item-list" v-for="innerItem of item" :key="innerItem.id">
          <div class="item border-bottom" @click="handleClickCity(innerItem.name)">{{innerItem.name}}</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import BScroll from 'better-scroll'
export default {
  name: 'CityList',
  props: {
    hot: Array,
    cities: Object,
    letter: String
  },
  methods: {
    handleClickCity (city) {
      this.$store.dispatch('changeCity', city)
      this.$router.push('/')
    }
  },
  watch: {
    letter () {
      if (this.letter) {
        const element = this.$refs[this.letter][0]
        console.log(this.$refs[this.letter][0])
        this.scroll.scrollToElement(element)
      }
    }
  },
  mounted () {
    this.scroll = new BScroll(this.$refs.warpper)
  }
}
</script>

<style lang="stylus" scoped>
  .border-topbottom
    &:before
      border-color: #cccccc
    &:after
      border-color: #cccccc
  .border-bottom
    &:before
      border-color: #cccccc
  .list
    overflow:hidden
    position: absolute
    top: 1.58rem
    left:0
    right:0
    bottom:0
    .title
      line-height: .54rem
      background: #eee
      padding-left: .2rem
      color: #666666
      font-size: .26rem
    .button-list
      overflow:hidden
      padding:.1rem .6rem .1rem .1rem
      .button-warpper
        width:33.33%
        float: left
        .button
          margin: .1rem
          padding: .1rem 0
          border: .02rem solid #ccc
          text-align: center
          border-radius: .06rem
    .item-list
      .item
        line-height: .76rem
        padding-left: .2rem
</style>
