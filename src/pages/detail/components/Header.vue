<template>
  <div>
    <router-link to="/" class="header-abs" v-show="showAbs">
      <div class="iconfont header-abs-back-icon">&#xe643;</div>
    </router-link>
    <div class="header-fixed"
         v-show="!showAbs"
         :style="opacityStyle"
    >
      <router-link to="/">
        <div class="iconfont header-fixed-back-icon">&#xe643;</div>
      </router-link>
      景点详情
    </div>
  </div>
</template>

<script>
export default {
  name: 'DetailHeader',
  data () {
    return {
      showAbs: true,
      opacityStyle: {
        opacity: 0
      }
    }
  },
  methods: {
    handleScroll () {
      const scrollTop = document.documentElement.scrollTop
      if (scrollTop > 60) {
        this.showAbs = false
        let opacity = scrollTop / 140
        opacity = opacity > 1 ? 1 : opacity
        this.opacityStyle = {opacity}
      } else {
        this.showAbs = true
      }
    }
  },
  activated () {
    window.addEventListener('scroll', this.handleScroll)
  },
  deactivated () {
    window.removeEventListener('scroll', this.handleScroll)
  }
}
</script>

<style lang="stylus" scoped>
  @import "~styles/varibles.styl"
  .header-abs
    position absolute
    top .2rem
    left .2rem
    width .5rem
    height .5rem
    line-height .5rem
    border-radius .25rem
    text-align center
    background rgba(0, 0, 0, .5)
    .header-abs-back-icon
      font-size .4rem
      color #fff
  .header-fixed
    position :fixed
    top 0
    left 0
    right 0
    height : $headerHeight
    line-height : $headerHeight
    background : $bgcolor
    text-align : center
    color : #fff
    font-size : .32rem
    .header-fixed-back-icon
      position absolute
      width: .64rem
      font-size : .4rem
      color #fff
</style>
