<script setup>
import { ref } from "vue"

const name = ref("黄朗轩")
const age = ref(18)
const city = ref("广州")

const move = () => {
  city.value = "深圳"
}
</script>

<template>
  <div>
    <div>姓名：{{ name }}</div>
    <div>年龄：{{ age }}</div>
    <div>城市：{{ city }}</div>
    <button @click="move">搬家</button>
  </div>
</template>
