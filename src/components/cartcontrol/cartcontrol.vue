<template>
  <div class="cartcontrol">
    <transition name="moveRight">
      <div class="cart-decrease inner icon-remove_circle_outline" v-show="food.count > 0" @click.stop.prevent="decreaseCart($event)"></div>
    </transition>
    <div class="cart-count" v-show="food.count > 0">{{food.count}}</div>
    <div class="cart-add icon-add_circle" @click.stop.prevent="addCart($event)"></div>
  </div>
</template>

<script type="text/ecmascript-6">
  import Vue from 'vue';

  export default {
    props: {
      food: {
        type: Object
      }
    },
    methods: {
      addCart(event) {
        if (!event._constructed) {
          return;
        }
        if (!this.food.count) {
          Vue.set(this.food, 'count', 1);
        } else {
          this.food.count++;
        }
        this.$emit('increment', event.target);
      },
      decreaseCart(event) {
        if (!event._constructed) {
          return;
        }
        if (this.food.count) {
          this.food.count--;
        }
      }
    }
  };
</script>

<style lang="stylus" rel="stylesheet/stylus">
  .cartcontrol
    font-size: 0
    .cart-decrease
      display: inline-block
      padding: 6px
      transition: all 0.4s linear
      opacity: 1
      transform: translate3d(0, 0, 0), rotate(0)
      line-height: 24px
      font-size: 24px
      color: rgb(0, 160, 220)
      transtion: all 0.4s linear
      &.moveRight-enter-active, &.moveRight-leave-active
        opacity: 0
        transform: translate(24px, 0) rotate(180deg)
        transtion: all 0.4s linear
      &.moveRight-enter, &.moveRight-leave-active
        opacity: 0
        transform: translate3d(0, 0, 0), rotate(0)
        transtion: all 0.4s linear
    .cart-count
      display: inline-block
      vertical-align: top
      width: 12px
      padding-top: 6px
      line-height: 24px
      text-align: center
      font-size: 10px
      color: rgb(147, 153, 159)
    .cart-add
      display: inline-block
      padding: 6px
      line-height: 24px
      font-size: 24px
      color: rgb(0, 160, 220)
</style>
