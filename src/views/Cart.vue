<template>
  <div>
    <div style="margin-bottom: 20px">
      商品名称：<input
        type="text"
        placeholder="请输入商品名称"
        v-model.trim="productName" />
      商品价格：<input
        type="text"
        placeholder="请输入商品价格"
        v-model.number="productPrice"
        @change="checkPrice" />
      商品库存：<input
        type="text"
        placeholder="请输入商品库存"
        v-model.number="productStock"
        @change="checkStock" />
      <button @click="addProduct">添加</button>
    </div>
    <table border="1" cellpadding="5" cellspacing="0">
      <tr>
        <th>
          <input type="checkbox" v-model="selectAll" @change="checkAll" />
        </th>
        <th>商品</th>
        <th>单价</th>
        <th>库存</th>
        <th colspan="2">操作</th>
      </tr>
      <tr
        v-for="(item, index) in list"
        :key="item.id"
        :style="{
          'background-color': item.checked ? 'gainsboro' : '#fff',
        }">
        <td>
          <input type="checkbox" v-model="item.checked" @change="updateAll" />
        </td>
        <td>{{ item.name }}</td>
        <td>{{ item.price }}</td>
        <td>{{ item.stock }}</td>
        <td>
          <button @click="sub(item)">-</button>
          <input
            class="num-input"
            :class="{
              'red-color': item.num === item.stock,
            }"
            type="number"
            v-model.number="item.num" />
          <button @click="add(item)">+</button>
        </td>
        <td>
          <button @click="remove(index)">删除</button>
        </td>
      </tr>

      <tr v-if="list.length === 0">
        <td colspan="6">购物车空空如也</td>
      </tr>

      <tr>
        <td colspan="6">
          <div>
            总价：<span>¥{{ totalPrice }}</span>
          </div>
          <div>总数：{{ totalNum }}</div>
        </td>
      </tr>
    </table>
  </div>
</template>

<script setup>
import { ref, reactive, computed } from "vue"

const list = reactive([
  {
    id: 1,
    name: "苹果",
    price: 5,
    num: 2,
    stock: 5,
    checked: false,
  },
  {
    id: 2,
    name: "香蕉",
    price: 10,
    num: 1,
    stock: 10,
    checked: true,
  },
  {
    id: 3,
    name: "橙子",
    price: 8,
    num: 3,
    stock: 10,
    checked: false,
  },
  {
    id: 4,
    name: "葡萄",
    price: 15,
    num: 1,
    stock: 10,
    checked: false,
  },
  {
    id: 5,
    name: "西瓜",
    price: 20,
    num: 1,
    stock: 10,
    checked: false,
  },
])

const add = (item) => {
  if (item.num < item.stock) {
    item.num++
  }
}

const sub = (item) => {
  if (item.num > 0) {
    item.num--
  }
}

const remove = (item) => {
  list.splice(item, 1)
}

const totalPrice = computed(() => {
  let total = 0
  const checkedItems = list.filter((item) => {
    return item.checked
  })
  //   checkedItems.forEach((item) => {
  //     total += item.price * item.num
  //   })
  //   return total

  return checkedItems.reduce((total, item) => {
    return total + item.price * item.num
  }, 0)
})

const selectAll = ref(false)

const checkAll = (e) => {
  list.forEach((item) => {
    item.checked = e.target.checked
  })
}

const updateAll = (e) => {
  const allChecked = list.every((item) => {
    return item.checked
  })
  selectAll.value = allChecked
}

const productName = ref("")
const productPrice = ref()
const productStock = ref()

const addProduct = (index) => {
  // 校验表单
  if (productName.value === "") {
    alert("请输入商品名称")
    return
  }
  // 如果没有填写商品价格
  if (productPrice.value === 0) {
    alert("请输入商品单价")
    return
  }
  // 如果没有填写商品库存
  if (productStock.value === 0 || typeof productStock.value !== "number") {
    alert("请输入库存数量")
    return
  }

  list.push({
    id: list.length + 1,
    name: productName.value,
    price: productPrice.value,
    num: 1,
    stock: productStock.value,
    checked: false,
  })

  // 清空表单
  productName.value = ""
  productPrice.value = null
  productStock.value = null
}

const checkPrice = (e) => {
  if (typeof productPrice.value !== "number") {
    alert(`请输入商品单价`)
    productPrice.value = null
  }
}

const checkStock = (e) => {
  if (typeof productStock.value !== "number") {
    alert(`请输入库存数量`)
    productStock.value = null
  }
}

const totalNum = computed(() => {
  const checkedItems = list.filter((item) => {
    return item.checked
  })

  return checkedItems.reduce((total, item) => {
    return total + item.num
  }, 0)
})
</script>

<style scoped>
table {
  width: 100%;
  text-align: center;
}

.red-color {
  color: red;
}

.num-input {
  width: 30px;
  text-align: center;
}
</style>
