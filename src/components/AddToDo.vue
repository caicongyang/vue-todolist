<template>
    <div>
      <input v-model="newTodo" @keyup.enter="submitTodo" placeholder="Add new todo" />
      <button @click="submitTodo">Add</button>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  
  const newTodo = ref('');
  const emit = defineEmits(['add-todo']); // 声明 emit 的事件名称

  const submitTodo = () => {
    if (newTodo.value.trim() !== '') {
      emit('add-todo', newTodo.value.trim());
      newTodo.value = '';
    }
  };
  </script>
  
  <style scoped>
  div {
    display: flex;
    justify-content: space-between;
    margin-bottom: 20px;
  }
  
  input {
    flex: 1;
    padding: 10px;
    font-size: 16px;
  }
  
  button {
    padding: 10px;
    font-size: 16px;
    margin-left: 10px;
    cursor: pointer;
  }
  </style>
  