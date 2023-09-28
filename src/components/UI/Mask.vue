<template>
  <!-- Teleport 可以将组件渲染到网页的指定位置 -->
  <Teleport to="body">
    <div
        :="$attrs" 
        class="mask" v-show="props.isShow"
        @click.self="$emit('hide')">   <!--这个self是为了防止冒泡发生，只有点击它自己时才会触发-->
        <slot></slot>
    </div>
  </Teleport>
  
</template>

<script setup>
import { ref } from 'vue'
const props = defineProps(['isShow'])
const emits = defineEmits(['hide'])//因为子组件最好不要修改传入的props
</script>

<style>
.mask {
    position: fixed;
    top:0;
    bottom: 0;
    left: 0;
    right: 0;
    background-color: rgba(0, 0, 0, 0.3);
    z-index: 99999;
}
</style>