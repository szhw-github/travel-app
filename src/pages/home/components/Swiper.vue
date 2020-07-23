<template>
  <div class="wrapper">
    <swiper :options="swiperOptions" v-if="showSwiper">
      <swiper-slide v-for="item of list" :key="item.id">
        <img class="swiper-img" :src="item.imgUrl"/>
      </swiper-slide>
      <div class="swiper-pagination" slot="pagination"></div>
    </swiper>
  </div>
</template>

<script>
export default {
  name: 'HomeSwiper',
  props: {
    list: Array
  },
  data () {
    return {
      notNextTick: true,
      swiperOptions: {
        pagination: '.swiper-pagination',
        preventClicks: false,
        loop: true,
        observer: true,
        observeParents: true,
        mousewheelControl: true
      }
    }
  },
  computed: {
    showSwiper () {
      return this.list.length
    }
  }
}

</script>

<style lang="stylus" scoped>
  .wrapper >>> .swiper-pagination-bullet-active
    background : #fff
  .wrapper
    overflow : hidden
    width : 100%
    height :0
    padding-bottom 31.25%
    .swiper-img
      width : 100%
</style>
