<template lang="html">
  <div class="supports" :class="supportsType">
    <div class="support-item" v-for="support in supports">
      <span class="icon" :class="classMap[support.type]"></span>
      <span class="text">{{support.description}}</span>
    </div>
  </div>
</template>

<script type="text/ecmascript-6">
export default {
  props: {
    supports: {
      type: Array
    },
    size: {
      type: Number
    }
  },
  data () {
    return {
      classMap: ['decrease', 'discount', 'special', 'invoice', 'guarantee']
    };
  },
  computed: {
    supportsType() {
      return 'supports-' + this.size;
    }
  }
};
</script>

<style lang="stylus" type="stylesheet/stylus">
@import "../../common/stylus/mixin.styl"
.supports
  .support-item
    padding: 0 12px
    margin-bottom: 12px
    font-size: 0
    &:last-child
      margin-bottom: 0
    .icon
      display: inline-block
      vertical-align: top
      background-size: cover
      background-repeat: no-repeat
    .text
      line-height: 12px
      font-size: 10px
  &.supports-1
    .support-item
      .icon
        width: 12px
        height: 12px
        margin-right: 4px
        &.decrease
          bg-image('decrease_1')
        &.discount
          bg-image('discount_1')
        &.guarantee
          bg-image('guarantee_1')
        &.invoice
          bg-image('invoice_1')
        &.special
          bg-image('special_1')
  &.supports-2
    .support-item
      .icon
        width: 16px
        height: 16px
        margin-right: 6px
        &.decrease
          bg-image('decrease_2')
        &.discount
          bg-image('discount_2')
        &.guarantee
          bg-image('guarantee_2')
        &.invoice
          bg-image('invoice_2')
        &.special
          bg-image('special_2')
  &.supports-3
    .support-item
      .icon
        &.decrease
          bg-image('decrease_3')
        &.discount
          bg-image('discount_3')
        &.guarantee
          bg-image('guarantee_3')
        &.invoice
          bg-image('invoice_3')
        &.special
          bg-image('special_3')
  &.supports-4
    .support-item
      .icon
        &.decrease
          bg-image('decrease_4')
        &.discount
          bg-image('discount_4')
        &.guarantee
          bg-image('guarantee_4')
        &.invoice
          bg-image('invoice_4')
        &.special
          bg-image('special_4')
</style>
