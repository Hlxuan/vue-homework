<template>
  <div>
    <ChildJob1 :userInfo="userInfo" :hobbies="hobbies"></ChildJob1>
  </div>
</template>

<style scoped></style>

<script setup>
import { ref } from "vue"
import ChildJob1 from "./ChildJob1.vue"

const userInfo = ref({
  name: "黄朗轩",
  email: "huanglangxuan@hlxuan.top",
  sex: "male",
})

const hobbies = ref(["篮球", "羽毛球"])
</script>
