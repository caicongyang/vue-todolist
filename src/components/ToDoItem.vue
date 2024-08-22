<template>
    <li>
      <span
        :style="{ textDecoration: todo.completed ? 'line-through' : 'none' }"
        @click="toggleComplete"
      >
        {{ todo.text }}
      </span>
      <button @click="deleteTodo">Delete</button>
    </li>
  </template>
  
  <script setup>
  defineProps({
    todo: Object,
    required: true
  });

  // 使用 defineEmits 声明 emit 事件
const emit = defineEmits(['delete-todo', 'toggle-complete']);

// 事件处理函数
const deleteTodo = () => {
  emit('delete-todo');
};

const toggleComplete = () => {
  emit('toggle-complete');
};
  </script>
  
  <style scoped>
  li {
    display: flex;
    justify-content: space-between;
    padding: 10px 0;
  }
  
  span {
    cursor: pointer;
    flex: 1;
  }
  
  button {
    background: none;
    border: none;
    color: red;
    cursor: pointer;
  }
  </style>
  