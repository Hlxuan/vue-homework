<script setup>
import { ref } from "vue"

const n1 = ref(2)
const n2 = ref(2)
</script>

<template>
  <div>
    <input type="text" v-model.number="n1" /> +
    <input type="text" v-model.number="n2" />
    =
    {{ n1 + n2 }}
  </div>
</template>
