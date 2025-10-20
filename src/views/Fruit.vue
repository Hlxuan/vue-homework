<template>
  <div>
    <h4>今日水果</h4>
    <ul>
      <li v-for="item in fruits" :key="item.id">
        <input type="checkbox" name="fruit" />
        {{ item.id }}. {{ item.name }}
        <button @click="deleteFruit(item.id)">删除</button>
      </li>
    </ul>
  </div>
</template>

<script setup>
import { ref } from "vue"

const fruits = ref([
  {
    id: 1,
    name: "苹果",
  },
  {
    id: 2,
    name: "香蕉",
  },
  {
    id: 3,
    name: "橙子",
  },
])

function deleteFruit(id) {
  fruits.value = fruits.value.filter((item) => item.id !== id)
}
</script>
