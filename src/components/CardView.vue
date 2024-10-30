<template>
  <section>
    <form @submit.prevent="addTodo">
      <input type="text" v-model="newTodo" />
      <button type="submit">Add</button>
    </form>
    <div v-for="todo in todos" :key="todo.id" class="card">
      <div>
        <button @click="doneTodo(todo.id)">
          <input type="checkbox" />
        </button>
      </div>
      <div class="card-content">
        <h1 class="text-content">{{ todo.text }}</h1>
        <p class="time-content">{{ todo.date }}</p>
      </div>
    </div>
    <div v-show="todos.length === 0" id="null-data">data kosong</div>
  </section>
</template>

<script setup lang="ts">
import { ref, Ref } from 'vue'

interface Todo {
  text: string
  todayLocale: number
}

let id: number = 1

const todayLocale = new Date().toLocaleDateString()

const newTodo = ref<string>('')
const todos: Ref<Todo>[] = ref([])

function addTodo() {
  if (newTodo.value.trim() !== '') {
    todos.value.push({
      id: id++,
      text: newTodo.value,
      date: todayLocale,
    })
    newTodo.value = ''
  } else{
    alert("Data tidak boleh kosong!")
  }
}

function doneTodo(todoID: number) {
  todos.value = todos.value.filter(t => t.id !== todoID)
}
</script>

<style scoped>
section {
  margin-top: 5px;
  width: 900px;
  display: grid;
  place-items: center;
}

#null-data {
  margin-top: 10px;
  text-align: center;
  font-family: 'Times New Roman', Times, serif;
  font-size: 12pt;
  font-weight: bold;
  color: red;
}

.card {
  display: flex;
  align-items: center;
  width: 300px;
  background: white;
  padding: 0.3em;
  border-radius: 6px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  height: 20px;
  margin-top: 12px;
}

.card-content {
  width: 100%;
  align-items: center;
  padding-left: 10px;
  padding-right: 10px;
  display: flex;
  justify-content: space-between;
}

.text-content {
  font-weight: 400 bold;
  font-size: 15pt;
  padding: 0px 20px 0 5px;
}

.time-content {
  font-size: 9pt;
  color: rgba(0, 0, 0, 0.795);
  font-weight: bold;
}
</style>
