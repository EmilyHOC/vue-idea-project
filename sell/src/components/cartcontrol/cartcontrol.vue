<template>
    <div class="cartcontrol">
        <div class="cart-decrease fa fa-minus-circle"  v-show="food.count>0"
             @click="decreaseCart" >
        </div>
        <div class="cart-count" v-show="food.count>0">{{food.count}}</div>
        <div class="cart-add fa fa-plus-circle"  aria-hidden="true" @click="addCart"></div>
    </div>
</template>

<script>
    import Vue from 'vue';
  export default {
    props: {
      food: {
        type: Object
      }
    },
    created () {
    },
    methods: {
      addCart (e) {
        if (!e._constructed) {
          return;
        }
        if (!this.food.count) {
          Vue.set(this.food, 'count', 1);
        }
        if (!this.food.count) {
          this.food.count = 1;
        } else {
          this.food.count++;
        }
      },
      decreaseCart (e) {
        if (!e._constructed) {
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
        font-size:0
        .cart-decrease,.cart-add
            display: inline-block
            padding: 6px
            line-height: 24px
            font-size: 24px
            color: rgb(0, 160, 220)

        .cart-count
            display: inline-block
            vertical-align: top
            width: 12px
            padding-top: 6px
            line-height: 24px
            text-align: center
            font-size: 10px
            color: rgb(147, 153, 159)
</style>
