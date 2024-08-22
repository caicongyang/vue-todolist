<template>
  <div id="app">
    <Header />
    <AddToDo @add-todo="addTodo" />
    <ToDoList
      :todos="todos"
      @delete-todo="deleteTodo"
      @toggle-complete="toggleComplete"
    />
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import Header from './components/Header.vue';
import AddToDo from './components/AddToDo.vue';
import ToDoList from './components/ToDoList.vue';

const todos = ref([]);

onMounted(() => {
  const savedTodos = JSON.parse(localStorage.getItem('todos') || '[]');
  todos.value = savedTodos;
});

const addTodo = (todoText) => {
  todos.value.push({ text: todoText, completed: false });
  saveTodos();
};

const deleteTodo = (index) => {
  todos.value.splice(index, 1);
  saveTodos();
};

const toggleComplete = (index) => {
  todos.value[index].completed = !todos.value[index].completed;
  saveTodos();
};

const saveTodos = () => {
  localStorage.setItem('todos', JSON.stringify(todos.value));
};
</script>

<style scoped>
#app {
  max-width: 600px;
  margin: 0 auto;
}
</style>
