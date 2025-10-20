<template>
  <h3>🍎 水果记事本</h3>
  <input placeholder="记下水果..." v-model="text" />
  <button @click="add">添加</button>
  <ul v-if="note.length > 0">
    <li v-for="(item, index) in note" :key="index">
      {{ item }}<button @click="remove(index)">删除</button>
    </li>
  </ul>
  <p v-else>暂无水果记录</p>

  <div>共{{ note.length }}条记录 <button @click="clear">清空</button></div>
</template>

<script setup>
import { ref } from "vue"

const text = ref("")
const note = ref([])

function add() {
  if (text.value.trim()) {
    note.value.push(text.value.trim())
    text.value = ""
  }
}

function remove(index) {
  note.value.splice(index, 1)
}

function clear() {
  note.value = []
}
</script>
