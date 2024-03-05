<script setup>
import { useTodoListStore } from '../stores/todoList.js'
import { storeToRefs } from 'pinia'

const store = useTodoListStore()

// storeToRefs lets todoList keep reactivity:
const { todoList } = storeToRefs(store)
const { toggleCompleted, deleteTodo } = store
</script>
<template>
  <div v-for="todo in todoList" :key="todo.id">
    <div class="todo-list">
      <span
        :class="{ completed: todo.completed }"
        class="todo-item"
        @click="toggleCompleted(todo.id)"
        >{{ todo.item }}</span
      >

      <span @click="deleteTodo(todo.id)">&#10060;</span>
    </div>
  </div>
</template>

<style scoped>
.completed {
  text-decoration: line-through;
  opacity: 0.6;
  font-weight: normal !important;
}
.todo-list {
  display: flex;
  width: 100%;
  padding: 2px 16px 2px 16px;
  align-items: center;
  justify-content: center;
}
.todo-item {
  margin-right: 24px;
  cursor: pointer;
  flex: 1;
  font-weight: bold;
}
span {
  cursor: pointer;
}
.item {
  display: flex;
  justify-content: center;
}
.todo-list:hover {
  box-shadow: 1px 1px 5px 1px #dadada;
  border-radius: 4px;
}
.content {
  display: flex;
  font-size: 1.5em;
  justify-content: space-between;
  width: 80vw;
  padding: 5px;
}
.completed {
  text-decoration: line-through;
}
</style>
