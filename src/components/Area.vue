<script setup>
import { ref } from 'vue'
const areas = ref(['nav','main','footer'])
</script>
<template>
    
    <p v-for="area in areas" :key="area" :class="area">
        <!-- 就是把父層的這段：<span>我現在在：{{ chosenArea }}</span>傳進來，slot是接口，:name會動態判斷要傳哪個值進來 -->
        <slot :name="area"></slot>
    </p>
     
</template>
<style>
    .nav{
        color: green;
    }
    .main{
        color: brown;
    }
    .footer{
        color: blue;
    }
</style>
