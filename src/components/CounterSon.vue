<template>
  <div>
    <button @click="addCount">计数器 +1</button>
  </div>
</template>

<style scoped></style>

<script setup>
import { ref } from "vue"

const count = ref(0)

const emit = defineEmits(["customEvent"])

const addCount = () => {
  count.value++
  emit("customEvent", count.value)
}
</script>
