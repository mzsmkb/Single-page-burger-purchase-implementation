<template>
  <div class="counter">

    <template v-if="props.meals.count > 0">
        <button class="sub" @click="$events=>meals.subMmealFromCart(props.meals)"><i class="ri-subtract-line"></i></button>
        <span class="count">{{props.meals.count}}</span>
    </template>
    
    <button class="add" @click="$events=>meals.addMealToCart(props.meals)"><i class="ri-add-line"></i> </button>
  </div>
</template>
 
<script setup>
import { ref } from 'vue'
import { useMealsStore } from '../../store/meals';

const count = ref(0)

const meals = useMealsStore()
const props = defineProps(["meals"])

</script>

<style>

.counter {
    display: flex;
    align-items: center;
    /* border-style: dotted; */
}

.sub,.add{
    display: flex;
    justify-content: center;
    border: none;
    align-items: center;
    border-radius: 50%;
    background-color: rgb(238, 184, 6);
    width: 36rem;
    height: 36rem;
    font-size: 36rem;
    font-weight: bold;
}

.sub{
    background-color: aliceblue;
    /* margin-right: 4px; */
    border: 1px sold #000;
    /* border-style:hidden; */
}
.count {
    margin: 0 10rem;
    font-size: 30rem;
}

</style>