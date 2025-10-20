<script setup>
import { ref, watch } from "vue"

const n1 = ref(0)
function add() {
  n1.value++
}

watch(n1, (newValue, oldValue) => {
  console.log("新数值", newValue, "旧数值", oldValue)
  if (newValue === 3) {
    console.log("变化了")
  }
})
</script>

<template>
  <div>
    <button @click="add">增加</button>
  </div>
</template>

<style scoped></style>
