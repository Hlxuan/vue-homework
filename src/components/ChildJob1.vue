<template>
  <div>
    <p>姓名：{{ userInfo.name }}</p>
    <p>邮箱：{{ userInfo.email }}</p>
    <p>性别：{{ userInfo.sex }}</p>
    <p>爱好：
        <ul>
            <li v-for="hobby in hobbies" :key="hobby">{{ hobby }}</li>
        </ul>
    </p>
  </div>
</template>

<script setup>
const props = defineProps({
  userInfo: {
    type: Object,
    required: true,
  },
  hobbies:{
    type: Array,
    required: true,
  }
})
</script>
