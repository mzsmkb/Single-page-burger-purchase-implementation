<template>
    <!-- 所有汉堡的容器 -->
  <div class="meals">
    <!-- 显示商品信息 -->
      <Meal 
        :desc="$attrs.desc"
        v-for="item in props.meals" :meals="item"></Meal>
    <h3 v-if=" !props.meals || props.meals.length === 0"> 没有找到相关的汉堡 </h3>
  </div>
  
</template>

<script setup>
const props = defineProps(['meals'])

import Meal from './Meal.vue';

import { useMealsStore } from '../../store/meals.js';

const meals = useMealsStore()


</script>

<style>

.meals {
    height: calc(100vh - 120rem);
    background-color: rgb(245, 240, 240);
    overflow: auto;
    padding-bottom: 140rem ;
}


</style>