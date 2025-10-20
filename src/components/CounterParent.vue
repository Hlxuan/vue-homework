<template>
  <div>
    <CounterSon @customEvent="receive"></CounterSon>
    <p>当前计数器值：{{ count }}</p>
  </div>
</template>

<style scoped></style>

<script setup>
import { ref } from "vue"
import CounterSon from "./CounterSon.vue"

const count = ref(0)

const receive = (val) => {
  console.log("父组件接收到的值：", val)
  count.value = val
}
</script>
