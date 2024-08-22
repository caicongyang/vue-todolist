<template>
    <ul>
      <ToDoItem
        v-for="(todo, index) in todos"
        :key="index"
        :todo="todo"
        @delete-todo="handleDeleteTodo(index)"
      @toggle-complete="handleToggleComplete(index)"
      />
    </ul>
  </template>
  
  <script setup>
  import ToDoItem from './ToDoItem.vue';
  
  defineProps({
    todos: Array,
    required: true

  });

  // 事件处理函数
const emit = defineEmits(['delete-todo', 'toggle-complete']);

const handleDeleteTodo = (index) => {
  emit('delete-todo', index);
};

const handleToggleComplete = (index) => {
  emit('toggle-complete', index);
};

  </script>
  
  <style scoped>
  ul {
    list-style: none;
    padding: 0;
  }
  </style>
  