<template>
  <div class="app">
    <h1>Todos</h1>
    <TaskForm @create="createTask" />
    <TaskList :tasks="tasks" @task-toggle="toggleTaskStatus" @task-delete="deleteTask" />
    <div>Невыполненные задачи: {{ incompleteTasksCount }}</div>
  </div>
</template>

<script>
import TaskForm from "@/components/TaskForm.vue";
import TaskList from "@/components/TaskList.vue";

export default {
  components: {
    TaskForm,
    TaskList,
  },
  data() {
    return {
      tasks: [
        { id: 1, title: 'Задача 1', done: false },
        { id: 2, title: 'Задача 2', done: false }
      ]
    };
  },
  computed: {
    incompleteTasksCount() {
      return this.tasks.filter(task => !task.done).length;
    }
  },
  methods: {
    createTask(task) {
      task.done = false;
      this.tasks.push(task);
    },
    toggleTaskStatus(index) {
      this.tasks[index].done = !this.tasks[index].done;
    },
    deleteTask(index) {
      this.tasks.splice(index, 1);
    }
  }
}
</script>
<style>
h1 {
  text-align: center
}

.app {
  width: 60vw;
  margin: 0 auto;
}
</style>