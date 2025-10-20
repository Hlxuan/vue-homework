<template>
  <!--无序列表，用于承载标签项-->
  <ul>
    <li v-for="(item, index) in list" :key="item.id" @click="gaoIndex = index">
      <a href="#" :class="{ active: index === gaoIndex }">{{ item.name }}</a>
    </li>
  </ul>
</template>

<script setup>
// 从Vue中引入ref函数，用于创建响应式数据
import { reactive, ref } from "vue"

const gaoIndex = ref(1)
const list = reactive([
  {
    name: "京东秒杀",
    id: 1,
  },
  {
    name: "每日特价",
    id: 2,
  },
  {
    name: "品类秒杀",
    id: 3,
  },
])
</script>

<style scoped>
/* 标签栏容器样式：flex布局使标签横向排列，底部红色边框，左右内边距10px */
ul {
  display: flex;
  border-bottom: 2px solid #e01222;
  padding: 0 10px;
  background-color: pink;
}
/* 标签项样式：固定宽高100px×50px，行高50px实现文字垂直居中，去除默认列表样式，文字水平居中 */
li {
  width: 100px;
  height: 50px;
  line-height: 50px;
  list-style: none;
  text-align: center;
}

/* 标签链接默认样式：块级显示（占满整个li），去除下划线，粗体，深灰色文字 */
li a {
  display: block;
  text-decoration: none;
  font-weight: bold;
  color: #333;
}

/* 高亮状态样式：红色背景，白色文字 */
li a.active {
  background-color: #e01222;
  color: #fff;
}
</style>
