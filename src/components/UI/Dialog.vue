<template>
    <Mask>
        <div class="dialog">
            <p class="msg">
                {{ props.msg }}
            </p>
            <div class="btn">
                <button @click="$emit('hide')" class="cancel">取消</button>
                <button @click="$emit('ok')" class="ok">确认</button>
            </div>
        </div>
    </Mask>
</template>

<script setup>
import { ref } from 'vue'
import Mask from './Mask.vue';

const props=defineProps(['msg'])
const emits = defineEmits(['ok'])

</script>

<style>
.dialog {
    position: absolute;
    width: 700rem;
    height: 400rem;
    background-color: aliceblue;
    border-radius: 40rem;
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;
    margin: auto;
}

.msg {
    height: 260rem;
    font-size: 40rem;
    text-align: center;
    line-height: 300rem;
}

.btn {
    display: flex;
    justify-content: space-around;
}

button {
    width: 300rem;
    height: 80rem;
    border-radius: 40rem;
    border: 1px solid #000;
    background-color: #fff;
    font-size: 32rem;
}

.ok {
    background-color: rgb(234, 149, 12);
    border: none;
}

</style>