<template>
  <div class="cartcontrol">
    <transition name="move">
      <div class="cart-decrease icon-remove_circle_outline" v-show="food.count>0"
      @click.stop="decreaseCart"></div>
    </transition>
    <div class="cart-count" v-show="food.count>0">{{ food.count }}</div>
    <div class="cart-add icon-add_circle" @click.stop="addCart"></div>
  </div>
</template>

<script type="text/ecmascript-6">
import Vue from 'vue'
export default {
  name: 'cartcontrol',
  props: {
    food: {
      type: Object
    }
  },
  created () {
  },
  methods: {
    addCart () {
      if (!this.food.count) {
        Vue.set(this.food, 'count', 1)
      } else {
        this.food.count++
      }
      this.$emit('cartAdd', event.target)
    },
    decreaseCart () {
      if (this.food.count) {
        this.food.count--
      }
    }
  }
}
</script>

<style lang="stylus" rel="stylesheet/stylus">
.cartcontrol
  font-size: 0
  .cart-decrease, .cart-add
    display: inline-block
    padding: 6px
    line-height: 24px
    font-size: 24px
    color: rgb(0,160,220)
    &.move-enter-active, &.move-leave-active {
      transition: all 0.4s linear
    }
    &.move-leave-to, &.move-enter {
      transform: translate3d(24px,0,0) rotate(180deg)
      opacity: 0
    }
  .cart-count
    display: inline-block
    vertical-align: top
    width: 12px
    padding-top: 6px
    line-height: 24px
    text-align: center
    font-size: 10px
    color: rgb(147,153,159)
  .cart-add
    display: inline-block
</style>
