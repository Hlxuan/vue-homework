<template>
  <div>
    <p>用户昵称：{{ userInfo.nickname }}</p>
    <p>用户等级：{{ userInfo.level }}</p>
  </div>
</template>

<style scoped></style>

<script setup>
import { inject } from "vue"

const userInfo = inject("userInfo")
console.log("BottomLevel组件中的userInfo：", userInfo)
</script>
