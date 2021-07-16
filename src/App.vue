<template>
  <div class="page">

    <div class="top-nav">
        <b-navbar toggleable="sm" type="dark" variant="dark" class="nav">
          <b-navbar-brand href="#">GS</b-navbar-brand>
          <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>
          <b-collapse id="nav-collapse" is-nav>
            <b-navbar-nav>
              <b-nav-item href="#">About</b-nav-item>
              <b-nav-item href="#" disabled>Work in progress</b-nav-item>
            </b-navbar-nav>
          </b-collapse>
        </b-navbar>
    </div>

    <div class="main-banner">
      <b-container fluid class="text-center">
        <h1>Hello</h1>
      </b-container>
    </div>

    <div class="widget d-flex justify-content-center">
      <b-card>
        <div class="task-tracker">
          <Header @toggle="toggle" title="Task tracker" :showNewTask="showNewTask" />
          <div v-if="showNewTask">
            <AddTask @add-task="addTask" />
          </div>
          <Tasks @delete-item="deleteItem" :tasks="tasks" />
        </div>
      </b-card>
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
.page {
  background: rgb(170, 135, 135);
}
.nav {
  padding-left: 10px !important;
  padding-right: 10px !important;
}
.main-banner {
  padding-top: 5vh;
  height: 20vh;
}
.widget {
  padding: 1rem;
  min-height: 80vh;
}
.task-tracker {
}
.btn {
  float: right;
  margin-right: 5px;
}
</style>
