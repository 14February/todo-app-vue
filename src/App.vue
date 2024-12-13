<script setup>
import { reactive, ref } from 'vue';

  const todoItem = ref('')
  const itemList = reactive([
  ])
  
  function add() {
    if (todoItem.value.trim() === '') {
      return;
    }
    itemList.push(todoItem.value)
    todoItem.value = ''
  }

  function deleteItem(index) {
    if (itemList.length === 0) {
      return;
    }
    itemList.splice(index, 1)
  }

  
  

</script>

<template>
  <div class="todoApp">
    <input type="text" v-model="todoItem" @keyup.enter="add" >
    <input type="button" @click="add" value="新增">
    <ul>
      <li v-for="(item, index) in itemList">{{ item }}<input type="button" @click="deleteItem(index)" value="删除"></li>
    </ul>
  </div>
  <span>总数：{{ itemList.length }}</span>
</template>

<style scoped>

</style>
