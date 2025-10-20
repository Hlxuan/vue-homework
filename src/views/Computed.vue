<template>
  <div>
    <h4>计算属性</h4>
    <p>{{ count }}</p>
    <button @click="add">增加</button>
    <button @click="sub">减少</button>
    <p>{{ doubleCount }}</p>
  </div>
</template>

<script setup>
import { ref, computed } from "vue"

const count = ref(0)
const doubleCount = computed(() => count.value * 2)

function add() {
  count.value++
}

function sub() {
  count.value--
}
</script>
