<template>

  <Checkout @close="showCheckout = false" :isShow="showCheckout"></Checkout>

  <Cartdetail 
  :isShow="showdetail"
  @hide="showdetail = false"
  ></Cartdetail>
  <div class="cart-bar">
    <div class="cart-bag">
      <img :src="cartBag" alt="">
      <span v-if="meals.totalCount > 0" class="total-count">{{meals.totalCount}}</span>
    </div>

    <div class="total-amount">
      <p v-if="meals.totalCount <= 0" class="no-goods">未选购商品</p>
      <p @click="showdetail=true" v-if="meals.totalCount > 0" class="has-goods">{{meals.amount}}</p>
    </div>

    <button @click="showCheckout = meals.totalCount > 0" class="checkout-btn"> 去结算</button>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import cartBag from "../../assets/bag.png"
import {useMealsStore} from '../../store/meals'
import Mask from '../UI/Mask.vue'

import Cartdetail from './Cartdetail.vue'
import Checkout from '../Checkout/Checkout.vue'

const meals = useMealsStore()

const showdetail = ref(false)
const showCheckout = ref(false)

</script>

<style>
.cart-bar {
  background-color: rgb(55, 57, 56);
  bottom: 40rem;
  width: 710rem;
  height: 100rem;
  position: fixed;
  left: 0;
  right: 0;
  margin: 0 auto;
  border-radius: 60rem;
  z-index: 9999;
}

.cart-bag{
  width: 80rem;
  position: absolute;
  bottom: -10rem;

}

.total-count{
  width: 40rem;
  height: 40rem;
  text-align: center;
  position:absolute;
  background-color: red;
  color: aliceblue;
  border-radius:50%;
  right: -20rem;
  top: 2rem;
  padding: 6rem;
  font-weight: bold; 
}


.total-amount{
  margin-left: 140rem;
  line-height: 100rem;
}

.no-goods,.has-goods {
  color: rgb(143, 145, 147);
  font-size: 28rem;
}

.has-goods{
  color: aliceblue;
  font-size: 32rem;
}
.has-goods::before {
  content: "￥";
  font-size: 20rem;
}

.checkout-btn{
  position: absolute;
  top: 0;
  right: 0;
  width: 200rem;
  height: 100%;
  border-radius: 60rem;
  border: none;
  background-color: rgb(255, 177, 7);
  font-size: 36rem;
}

</style>