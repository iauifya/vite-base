<script setup>
import CountCom from './components/count.vue'
import CardCom from './components/Card.vue'
import ProductCardCom from './components/ProductCard.vue'
import AreaCom from './components/Area.vue'
import {ref} from 'vue'

const sections = ref([
  {
    title: "限時優惠",
    slogan: "搶購限時最便宜貨品！",
  },
  {
    title: "最新商品",
    slogan: "為你帶來最新貨品！",
  },
  {
    title: "一般商品",
    slogan: "多種商品任你選擇！",
  },
])
const products = ref([
  {
    title: "夏日短裙",
    price: 200,
    sizes: ["XS", "S", "M", "L"],
  },
  {
    title: "純白 T-shirt",
    price: 100,
    sizes: ["XS", "S"],
  },
  {
    title: "針織背心",
    price: 300,
    sizes: ["XS", "S", "M"],
  },
])
const chosenArea = ref('nav')
const areas = ref(['nav','main','footer'])
</script>

<template>
  <div>
    <!-- <a href="https://vitejs.dev" target="_blank">
      <img src="/vite.svg" class="logo" alt="Vite logo" />
    </a>
    <a href="https://vuejs.org/" target="_blank">
      <img src="./assets/vue.svg" class="logo vue" alt="Vue logo" />
    </a> -->
  </div>
  
  <!-- 動態slot範例，component為Area.vue -->
  <div v-for="(area,index) in areas" :key="area">
      <input type="radio" v-model="chosenArea" :value="area">
      <label :for="area">{{ area }}</label>
  </div>
  <AreaCom>
    <template v-slot:[chosenArea]>
        <span>我現在在：{{ chosenArea }}</span>
    </template>
  </AreaCom>

  <!-- 具名slot範例，利用 slot 打造自己的 UI 元件，component為Card.vue -->
  <CardCom v-for="section in sections" :key="section.title">
    <template #title>
      {{ section.title }}
    </template>
    <template #slogan>
      <h5>{{ section.slogan }}</h5>
    </template>
    <template #default>
      <p>其他詳細資訊</p>
    </template>
  </CardCom>

  <!-- 作用域插槽(scoped slot)， -->
  <ProductCardCom v-for="product in products" :key="product.title">
    <template #title>
      {{ product.title }}
    </template>
    <template #price>
      {{ product.price }}
    </template>
    <template #sizes>
      {{ product.sizes.join(",") }}
    </template>
    <template #result="slotProps">
        已選購：{{product.title}} X {{ slotProps.quantity }} 
        <!-- slotProps.quantity是由子元件那邊傳過來的 -->
    </template>
  </ProductCardCom>

  <CountCom />
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}

.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}

.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
