<template>
  <div>
    <MiddleLevel></MiddleLevel>
  </div>
</template>

<style scoped></style>

<script setup>
import { ref, provide } from "vue"
import MiddleLevel from "./MiddleLevel.vue"

const userInfo = ref({
  nickname: "黄朗轩",
  level: "超级VIP",
})
provide("userInfo", userInfo)
console.log("TopLevel组件中的userInfo：", userInfo)
</script>
