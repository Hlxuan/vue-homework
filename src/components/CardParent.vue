<template>
  <div>
    <CardComponentVue>
      <template #cardHeader>
        <h1>这是一个标题</h1>
      </template>
      <template #default>
        <p>请在这里输入卡片的内容。</p>
      </template>
      <template #cardFooter>
        <button>查看详情</button>
      </template>
    </CardComponentVue>
  </div>
</template>

<style scoped></style>

<script setup>
import CardComponentVue from "./CardComponent.vue.vue"
</script>
