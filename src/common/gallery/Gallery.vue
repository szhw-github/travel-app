<template>
  <div class="container" @click="handleGalleryClick">
    <div class="wrapper">
      <swiper :options="swiperOptions">
        <swiper-slide
          v-for="(item, index) in imgs"
          :key="index">
          <img class="swiper-img" :src="item"/>
        </swiper-slide>
      </swiper>
      <div class="swiper-pagination" slot="pagination"></div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CommonGallery',
  props: {
    imgs: {
      type: Array,
      default () {
        return []
      }
    }
  },
  data () {
    return {
      swiperOptions: {
        pagination: '.swiper-pagination',
        paginationType: 'fraction',
        observeParents: true,
        observer: true
      }
    }
  },
  methods: {
    handleGalleryClick () {
      this.$emit('close')
    }
  }
}
</script>

<style lang="stylus" scoped>
  .container >>> .swiper-pagination
    overflow inherit
  .container
    display flex
    flex-direction column
    justify-content center
    position fixed
    left 0
    right 0
    top 0
    bottom 0
    background #000
    .wrapper
      overflow hidden
      height 0
      width 100%
      padding-bottom 100%
      .swiper-img
        width 100%
      .swiper-pagination
        color #fff
</style>
