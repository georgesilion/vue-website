<template>
  <div>
    <div class="task-tracker">
      <Header @toggle="toggle" title="Task tracker" :showNewTask="showNewTask" />
      <div v-if="showNewTask">
        <AddTask @add-task="addTask" />
      </div>
      <Tasks @delete-item="deleteItem" :tasks="tasks" />
    </div>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Tasks from './components/Tasks.vue'
import AddTask from './components/AddTask.vue'

export default {
  name: 'App',
  components: {
    Header,
    Tasks,
    AddTask
  },
  data() {
    return {
      tasks: [],
      showNewTask: false
    }
  },
  methods: {
    toggle() {
      this.showNewTask = !this.showNewTask
    },
    addTask(task) {
      this.tasks = [...this.tasks, task]
    },
    deleteItem(id) {
      this.tasks = this.tasks.filter((task) => task.id !== id)
    }
  },
  created() {
    this.tasks = [
      {
        id: 1,
        text: 'Appointment',
        day: ' March 1st at 2:35pm'
      } 
    ]
  }
}
</script>

<style>
.task-tracker {
  font-family: Verdana, Geneva, Tahoma, sans-serif;
  border: 1px solid steelblue;
  max-width: 400px;
  padding: 10px;
}
.btn {
  float: right;
  color: #fff;
  border: none;
  padding: 10px 12px;
  margin-right: 5px;
  cursor: pointer;
}
</style>
