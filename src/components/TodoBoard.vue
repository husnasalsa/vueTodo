<script setup>
import TodoItems from './TodoItems.vue'
import { reactive } from 'vue'
const state = reactive({
  todo: '',
  date: ''
})
defineProps(['todos'])
const emit = defineEmits(['addTodo', 'deleteTodo', 'changeStatusTodo'])

function deleteTodo(index) {
  emit('deleteTodo', index)
}
function changeStatusTodo(index) {
  emit('changeStatusTodo', index)
}
</script>

<template>
  <div class="todoBoard">
    <div class="container w-100 card py-2 my-5">
        <h1 class="text-center p-3">My Todo-s</h1>
        <div class="row mx-3">
            <div class="col-5">
                <input 
                    v-model="state.todo"
                    class="form-control"
                    placeholder="Add new..."
                />
            </div>
            <div class="col-5">
                <input
                    type="date"
                    v-model="state.date"
                    class="form-control"/>
            </div>
            <div class="col-2">
              <button class="btn btn-primary w-100" @click="$emit('addTodo', state.todo, state.date)">Add</button>
            </div>
            <TodoItems class="mt-3" v-for="(todo, index) in todos" :key="todo.id" @deleteTodo="deleteTodo" @changeStatusTodo="changeStatusTodo" :todo="todo" :index="index"></TodoItems>
        </div>
    </div>
  </div>
</template>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
