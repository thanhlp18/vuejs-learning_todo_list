<script setup>
import { useTodoListStore } from '@/stores/todoList.js'
import { ref } from 'vue'
const todo = ref('')
const store = useTodoListStore()

function addItemAndClear(item) {
  if (item.length === 0) {
    return
  }
  // invokes function in the store:
  store.addTodo(item)
  todo.value = ''
}
</script>

<template>
  <form @submit.prevent="addItemAndClear(todo)">
    <input v-model="todo" type="text" /><button>Add</button>
  </form>
</template>
<style scoped>
form {
  display: flex;
  flex-direction: row;
  align-items: center;
  padding: 8px 16px;
}
input {
  height: 20px;
  width: 50%;
  flex: 1;
}
button {
  margin-left: 12px;
  background-color: #2f6089;
  padding: 5px 10px;
  border: none;
  border-radius: 5px;
  font-weight: 800;
  color: white;
  width: fit-content;
}
.alert-div {
  min-height: 25px;
}
.alert {
  color: #d1495b;
  font-size: 1em;
  font-weight: 600;
}
</style>
