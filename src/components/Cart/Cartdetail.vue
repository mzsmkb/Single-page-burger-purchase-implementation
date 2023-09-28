<template>

    <!-- 这里的mask是根组件，所以可以通过cartbar直接透传到这里 -->
  <Mask style="z-index: 999">
    <Dialog 
        @ok="okHandler"
        msg="确认清空购物车吗"
        @hide="showDialog = false" :is-show="showDialog"></Dialog>
    <div class="cart-detail">
        <div class="header">
            <h2>餐品详情</h2>
            <a @click="showDialog = true" href="javascript:;">
                <i class="ri-delete-bin-line"></i>
                清空购物车
            </a>
        </div>
            <Meals :desc="false" :meals="meals.cartMeals"></Meals>
        
    </div>
  </Mask>
</template>

<script setup>
import { ref } from 'vue'
import Mask from '../UI/Mask.vue';
import Meals from '../Meals/Meals.vue'
import Dialog from '../UI/Dialog.vue';
import { useMealsStore } from '../../store/meals';
const meals = useMealsStore()
const emits =defineEmits()
const showDialog = ref(false)


const okHandler = () =>{
    /*
        1\把购物车清空
         meals.clearCart（）
        2\关闭对话框 dialog

        3\关闭CartDetails
    */
    meals.clearCart()
    showDialog.value = false
    emits("hide")


}

</script>

<style scoped>
.cart-detail {
    background-color: rgb(255, 255, 255);
    position: absolute;
    bottom: 0;
    width: 750rem;
    border-top-right-radius: 40rem;
    border-top-left-radius: 40rem;
}

.meals {
    height: auto;
    max-height: calc(280rem *4);
}

.header {
    display: flex;
    justify-content: space-between;
    padding: 10rem 30rem 0;
}

.header a {
    color: rgb(193, 194, 195);
}
</style>