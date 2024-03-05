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

<style>
.completed {
  text-decoration: line-through;
  opacity: 0.6;
}
.todo-list {
  display: flex;
  width: 100%;
  padding: 4px 16px 0px 16px;
}
.todo-item {
  margin-right: 24px;
  cursor: pointer;
  flex: 1;
}
</style>
<style scoped>
span {
  cursor: pointer;
}
.item {
  display: flex;
  justify-content: center;
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
