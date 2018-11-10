<template>
  <div>
    <div class="banner" @click="handleBannerClick">
      <img class="banner-img" :src="bannerImg" />
      <div class="banner-info">
        <div class="banner-title">
          {{this.sightName}}
        </div>
        <div class="banner-number">
          <span class="iconfont banner-icon">&#xe651;</span>
          {{this.gallaryImgs.length}}
        </div>
      </div>
    </div>
    <fade-animation>
      <common-gallary :imgs="imgUrl" v-show="showGallary" @close="handleGallaryClick" :gallaryImgs="gallaryImgs"></common-gallary>
    </fade-animation>
  </div>
</template>

<script>
import CommonGallary from '../../../common/gallary/Gallary'
import FadeAnimation from '../../../common/fade/FadeAnimation'
export default {
  name: 'DetailBanner',
  components: {
    FadeAnimation,
    CommonGallary
  },
  props: {
    sightName: String,
    bannerImg: String,
    gallaryImgs: Array
  },
  data () {
    return {
      showGallary: false,
      imgUrl: ['http://img1.qunarzz.com/sight/p0/1411/38/217a6ffc968923cd95404a9b1e9e85e8.water.jpg_r_800x800_a67f524e.jpg', 'http://img1.qunarzz.com/sight/p0/1411/e2/054836aeec12503879a5a4efa9c0ca75.water.jpg_r_800x800_2b124f5d.jpg']
    }
  },
  methods: {
    handleBannerClick () {
      this.showGallary = true
    },
    handleGallaryClick () {
      this.showGallary = false
    }
  }
}
</script>

<style lang="stylus" scoped>
  .banner
    position: relative
    overflow:hidden
    height:0
    padding-bottom:55%
    .banner-img
      width:100%
    .banner-info
      display:flex
      position:absolute
      left:0
      right:0
      bottom:0
      line-height: .6rem
      color: #ffffff
      background-image: linear-gradient(top, rgba(0, 0, 0, 0), rgba(0, 0, 0, 0.8))
      .banner-title
        flex:1
        font-size: .32rem
        padding:0 .2rem
      .banner-number
        padding:0 .3rem
        margin-top: .14rem
        height: .32rem
        line-height: .32rem
        border-radius:.2rem
        background: rgba(0, 0, 0, .7)
        font-size: .24rem
        .banner-icon
          font-size:.24rem
</style>
