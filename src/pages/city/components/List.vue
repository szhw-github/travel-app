<template>
  <div class="list" ref="wrapper">
    <div>
      <div class="area">
        <div class="title border-topbottom">当前城市</div>
        <div class="button-list">
          <div class="button-wrapper">
            <div class="button">
              {{this.currentCity}}
            </div>
          </div>
        </div>
      </div>
      <div class="area">
        <div class="title border-topbottom">热门城市</div>
        <div class="button-list">
          <div class="button-wrapper"
               v-for="item in hotCities"
               :key="item.id"
               @click="handleCityClick(item.name)"
            >
            <div class="button">{{item.name}}</div>
          </div>
        </div>
      </div>
      <div class="area" v-for="item in cities" :key="item.title" :ref="item.title">
        <div class="title border-topbottom">{{item.title}}</div>
        <div class="item-list">
          <div class="item border-bottom"
               v-for="(city,index) of item.lists"
               :key="index"
               @click="handleCityClick(city)"
          >
            {{city}}
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import BScroll from 'better-scroll'
import {mapState, mapMutations} from 'vuex'
export default {
  name: 'CityList',
  props: {
    hotCities: Array,
    cities: Array,
    letter: String
  },
  methods: {
    handleCityClick (city) {
      this.changeCity(city)
      this.$router.push('/')
    },
    ...mapMutations(['changeCity'])
  },
  computed: {
    ...mapState({
      currentCity: 'city'
    })
  },
  watch: {
    letter () {
      if (this.letter) {
        const element = this.$refs[this.letter][0]
        this.scroll.scrollToElement(element)
      }
    }
  },
  mounted () {
    this.$nextTick(() => {
      this.scroll = new BScroll(this.$refs.wrapper, {
        click: true
      })
    })
  }
}
</script>

<style lang="stylus" scoped>
  .border-topbottom
    &:before
      border-color : #ccc
    &:after
      border-color : #ccc
  .border-bottom
    &:before
      border-color : #ccc
  .list
    overflow: hidden
    position: absolute
    top: 1.58rem
    left: 0
    right: 0
    bottom: 0
    .title
      line-height : .54rem
      background : #eee
      padding-left : .2rem
      color : #666
    .button-list
      overflow: hidden
      padding: .1rem
      padding-right: .4rem
      .button-wrapper
        float: left;
        width: 33.33%;
        .button
          margin: .1rem
          border: .02rem solid #ccc
          padding: .1rem
          color: #666
          text-align: center
          border-radius: .06rem
    .item-list
      .item
        padding: .1rem
        padding-left: .2rem
</style>
