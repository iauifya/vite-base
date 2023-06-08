<template>
    <div>
        <p>{{ count }}</p>
        <button @click="increment">增加1</button>
    </div>
</template>
<script setup>
//這裡的做法是把useTestStore.js用解構函數的方式取出useCounterStore import進來
//在利用變數store去拿到資料，拿回來資料後就可以用到component中
//state、getters得資料會透過computed來取得
//action函式透過function取得
//所以當action的函式(store.increment)透過function(increment)來修改store的狀態時，pinia會自動跟蹤這些修改，也就是說state.count會跟著改變，連帶count也會改變
//所以說 就不需要再透過mutation的方式在把改變過的資料存回去state中
import { computed } from 'vue'
import { useCounterStore } from '../store/useTestStore.js'
const store = useCounterStore()
const count = computed(()=> store.count)
function increment(){
    store.increment()
}
</script>