<template>
  <div>
    <div class="banner">

      <img class="banner-img" src="https://img1.qunarzz.com/travel/d7/1809/2e/de8d8fe9c37f87b5.jpg_r_1360x1360x95_54efdfb8.jpg">
      <div class="banner-info">
        <div class="banner-title">
          驾一叶扁舟，寻瓯江往事
        </div>
        <div class="banner-number" @click="handleBannerClick">
          <span class="iconfont banner-icon">&#xe678;</span>
          39
        </div>
      </div>
    </div>
    <common-gallery
      :imgs="imgs"
      v-show="showGallery"
      @close="handleGalleryClose"
    >
    </common-gallery>
  </div>
</template>

<script>
import CommonGallery from 'common/gallery/Gallery'
export default {
  name: 'DetailBanner',
  data () {
    return {
      showGallery: false,
      imgs: [
        'https://img1.qunarzz.com/travel/d5/1807/f7/4b6cfebbd2f794b5.jpg_r_1360x1360x95_6d5ce953.jpg',
        'https://img1.qunarzz.com/travel/d1/1807/84/3b721cfe25b7c5b5.jpg_r_1360x1360x95_daeda473.jpg'
      ]
    }
  },
  computed: {
  },
  methods: {
    handleBannerClick () {
      this.showGallery = true
    },
    handleGalleryClose () {
      this.showGallery = false
    }
  },
  components: {
    CommonGallery
  }
}
</script>

<style lang="stylus" scoped>
  .banner
    position relative
    overflow hidden
    height 0
    padding-bottom 55%
    .banner-img
      width 100%
    .banner-info
      display flex
      position absolute
      left 0
      right 0
      bottom 0
      line-height .6rem
      color #fff
      background-image linear-gradient(top, rgba(0, 0, 0, 0), rgba(0, 0, 0, .8))
      .banner-title
        flex 1
        font-size .32rem
        padding 0 .2rem
      .banner-number
        height .32rem
        line-height .32rem
        background rgba(0, 0, 0, .5)
        padding 0 .2rem
        margin-top .2rem
        border-radius .2rem
        font-size .24rem
        .banner-icon
          font-size .24rem
</style>
