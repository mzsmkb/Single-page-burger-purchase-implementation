<template>
    <div class="meal">
        <div class="img">
            <img :src="props.meals.img" :alt="meals.id">
        </div>

        <!-- 试验git的注释 -->
        <div class="info">
            <div class="desc">
                <h2>{{ props.meals.title }}</h2>
                <p v-show="props.desc">{{ props.meals.desc }}</p>
            </div>

            <div class="price-btn">
                <span class="price">{{ props.meals.price }}</span>
                <Counter :meals="props.meals"></Counter>
            </div>

        </div>
        
        
    </div>
    

</template>

<script setup>
import { ref } from 'vue'
import Counter from '../UI/Counter.vue'
const props = defineProps(['meals','desc'])

const meals=props.meals


</script>

<style scoped>

.meal {
    display: flex;
    height: 300rem;
    align-items: center;
    border-bottom: 1px rgb(151, 149, 149) solid;
    padding: 0 20rem;
}

.img {
    width: 200rem;
}

.info {
    width: 450rem;
    margin-left: 20rem;
}

.info h2{
    color: black;
    font-size: 30rem;
    font-weight: normal;
} 

.info p {
    font-size :24rem ;
    color: rgb(74, 74, 74);
}

.price-btn {
    display: flex;
    margin-top: 40rem;
    justify-content: space-between;
}

.price {
    font-size: 30rem;
    font-weight: bold;
}

.price::before{
    content: "￥";
}

</style>