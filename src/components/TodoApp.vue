<script setup>
import TodoForm from '@/components/TodoForm.vue'
import TodoList from '@/components/TodoList.vue'
</script>

<template>
  <div class="todo-app">
    <h3>Todos Nè</h3>
    <TodoForm />
    <TodoList />
  </div>
</template>
<style scoped>
.todo-app {
  padding: 5vh;
  min-height: 60vh;
  width: 50vw;
  margin: auto;
  background-color: #f7f9fc;
  box-shadow: 1px 1px 5px 1px #eaeaea;
}

.todo-app h3 {
  text-align: center;
}
</style>
