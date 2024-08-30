<script setup>
import { ref } from 'vue'

const newTodo = ref('')
const todos = ref([
  { id: 0, text: 'Learn HTML' },
  { id: 1, text: 'Learn JavaScript' },
  { id: 2, text: 'Learn Vue' }
])

function addTodo() {
  todos.value.push({ id: todos.value.length, text: newTodo.value })
  newTodo.value = ''
}

function removeTodo(todo) {
  todos.value = todos.value.filter((t) => t !== todo)
}
</script>

<template>

<div :class="$style.frame">
    <div :class="$style.head">
      TO DO APP
    </div>
    <div :class="$style.form">
      <form @submit.prevent="addTodo">
        <input v-model="newTodo" required placeholder="new todo" :class="$style.input">
        <button :class="$style.btn + ' ' + $style.btnAdd">Add Todo</button>
      </form>
    </div>
    <div :class="$style.todo">
      <ul>
        <li v-for="todo in todos" :key="todo.id" :class="$style.li">
          {{ todo.text }}
          <button :class="$style.btn + ' ' + $style.btnRemove" @click="removeTodo(todo)">X</button>
        </li>
      </ul>
    </div>
  </div>

  
</template>

<style module>

.frame {
  background-color: black;
  font-size: 16px;
  font-family: Arial, sans-serif;

  min-width: 100vw;
  min-height: 100vh;
  padding: 20px;
  box-sizing: border-box;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

.head {
  text-align: center;
  margin-bottom: 20px;
}
form {
  display: flex;
  flex-direction: column;
  align-items: center; /* İçeriği ortalar */
}

.form {
  margin-bottom: 20px;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.input {
  width: 100%;
  padding: 10px;
  font-size: 16px;
  border: 1px solid #ccc;
  border-radius: 4px;
  margin-bottom: 10px;
}

.btn {
  padding: 10px 15px;
  font-size: 25px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.btnAdd {
  background-color: #1B0C1A;
  color: white;
}

.btnAdd:hover {
  background-color: #4B2138;
}

.btnRemove {
  background-color: #2d222f;
  color: white;
}

.btnRemove:hover {
  background-color: #765d67;
}

.todo {
  max-width: 600px;
  margin: 0 auto;
  text-decoration-color: #a8bdcf;
  
}

ul {
  list-style: none;
  padding: 0;
}

.li {
  color: #000000;
  padding: 10px;
  margin: 5px 0;
  background-color: #FADCD5;
  border: 1px solid #ddd;
  border-radius: 4px;
  display: flex;
  font-family: Arial, Helvetica, sans-serif;
  font-weight: bolder;
  justify-content: space-between;
  align-items: center;
  transition: background-color 0.3s ease;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.li:hover {
  background-color: #6d3c52;
}
#app{
  background-color: #000000;}
body{
  background-color: #000000;
}
@media (max-width: 768px) {
  
  .form {
    flex-direction: column;
    align-items: center;
    margin-bottom: 20px;
  }

  .input {
    width: 100%;
    margin-bottom: 10px;
  }

  .btn {
    width: 100%;
  }
}
</style>