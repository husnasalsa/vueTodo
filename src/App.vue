<script setup>
import TodoBoard from './components/TodoBoard.vue'
import { reactive } from 'vue'
const state = reactive({
  todos: []
})
function addTodo(todo, date) {
  const newTodo = {
    id: state.todos.length + 1,
    content: todo,
    date: date,
    status: false
  }
  state.todos.push(newTodo)
}
function deleteTodo(id) {
  state.todos.splice(id, 1)
}
function changeStatusTodo(id) {
  state.todos[id].status = !state.todos[id].status
}
</script>

<template>
  <div id="app">
    <TodoBoard :todos="state.todos" @deleteTodo="deleteTodo" @addTodo="addTodo" @changeStatusTodo="changeStatusTodo" />
  </div>
</template>

<style>
body {
  background-color: azure;
}
</style>
