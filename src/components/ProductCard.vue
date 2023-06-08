<template>
    <div class="card product">
        <h3 class="title">
            <slot name="title"></slot>
        </h3>
        <p class="price">
            <slot name="price"></slot>
        </p>
        <p>
            <slot name="sizes"></slot>
        </p>
        <div class="quantity">
            <div>數量: {{ quantity }}</div>
            <select v-model="quantity">
                <option v-for="option in options" :value="option.value">
                    {{ option.text }}
                </option>
            </select>
        </div>
        <h4 class="result">
            <slot name="result" :quantity="quantity"></slot>
        </h4>
        <button>確認</button>
    </div>
</template>
<script setup>
import { ref } from 'vue'
const quantity = ref(0)

const options = ref([
    { text: '請選擇', value: 0 },
    { text: '一個', value: 1 },
    { text: '兩個', value: 2 },
    { text: '三個', value: 3 }
])
</script>