<template>
  <div class="header">
    <div class="header-left">
      <div class="iconfont back-icon">&#xe643;</div>
    </div>
    <div class="header-input">
      <span class="iconfont">&#xe60c;</span>
      <input type="text" placeholder="输入城市/景点/游玩主题">
    </div>
    <router-link to="/city">
      <div class="header-right">
        {{this.currentCity}}
        <span class="iconfont arrow-icon">&#xe644;</span>
      </div>
    </router-link>
  </div>
</template>

<script>
import {mapState} from 'vuex'
export default {
  name: 'HomeHeader',
  computed: {
    ...mapState({
      currentCity: 'city'
    })
  }
}
</script>

<style lang="stylus" scoped>
  @import "~styles/varibles.styl"
  .header
    display: flex
    line-height: .86rem
    color: #fff
    background: $bgcolor
    .header-left
      width: .64rem
      float: left
      .back-icon
        text-align : center
        font-size : .4rem
    .header-input
      flex: 1
      height :.62rem
      line-height : .62rem
      margin-top : .12rem
      margin-left : .2rem
      padding-left : .2rem
      background: #fff
      border-radius: .1rem
      color:#ccc
    .header-right
      min-width: 1.04rem
      padding: .1rem
      float: right
      text-align:center
      color : #fff
      .arrow-icon
        font-size : .2rem
        margin-left : -.05rem
</style>
