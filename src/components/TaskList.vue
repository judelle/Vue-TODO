<template>
    <div>
      <div class="task" v-for="(task, index) in tasks" :key="task.id" :class="{ done: task.done }">
        <div :class="{ doneText: task.done }">{{ task.title }}</div>
        <div class="buttons">
          <button class="toggleButton" @click="toggleTask(index)">
            <span v-if="task.done" class="checkmark">✔</span>
          </button>
          <button @click="deleteTask(index)">Удалить</button>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      tasks: {
        type: Array,
        required: true,
      }
    },
    methods: {
      toggleTask(index) {
        this.$emit('task-toggle', index);
      },
      deleteTask(index) {
        this.$emit('task-delete', index);
      }
    }
  }
  </script>
  
  <style scoped>
  .task {
    position: relative;
    padding: 15px;
    border: 2px solid teal;
    margin-top: 15px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    transition: background-color 0.3s ease, color 0.3s ease;
  }
  
  .done {
    background-color: #e0e0e0;
    color: gray;
  }
  
  .done::after {
    background-color: #e0e0e0;
    color: gray;
  }
  
  .buttons {
    display: flex;
  }
  
  .toggleButton {
    width: 24px;
    height: 24px;
    border-radius: 50%;
    border: 2px solid teal;
    display: flex;
    align-items: center;
    justify-content: center;
    cursor: pointer;
    margin-right: 5px;
  }
  
.checkmark {
    color: teal;
    font-size: 16px;
  }
  
  .toggleButton:hover {
    background-color: #e0e0e0;
  }
  
  .buttons button {
    padding: 5px 10px;
    cursor: pointer;
  }
  </style>
  