<template>
    <div>
      <div class="wrapper">
        <div class="item"
             v-for="(item, index) in list"
             :key="index"
        >
          <div class="item-title">
            <span class="item-title-icon"></span>
            {{item.title}}
          </div>
        </div>
      </div>
    </div>
</template>

<script>
export default {
  name: 'DetailList',
  props: {
    list: Array
  }
}
</script>

<style lang="stylus" scoped>
  .wrapper
    padding .2rem
    .item-title
      margin 0 .2rem .2rem 0

</style>
