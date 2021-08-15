<template>
  <div class="bg-secondary" id="main">

    <div class="top-nav">
        <b-navbar toggleable="sm" type="dark" variant="dark" class="nav">
          <b-navbar-brand href="#main">GS</b-navbar-brand>
          <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>
          <b-collapse id="nav-collapse" is-nav>
            <b-navbar-nav>
              <b-nav-item href="#task-tracker">Task Tracker</b-nav-item>
              <b-nav-item href="#todo">ToDo</b-nav-item>
            </b-navbar-nav>
          </b-collapse>
        </b-navbar>
    </div>

    <div class="main-banner text-center text-light">
        <h1>Hello</h1>
    </div>

    <div class="d-flex justify-content-center" id="todo">
      <b-card>
        <Header @toggle="toggleNewTodo" title="To Do" :showNewTodo="showNewTodo" />
        <div v-if="showNewTodo">
          <AddTodo @add-todo="addTodo" />
        </div>
        <Todos :todos="todos"/>
      </b-card>
    </div>

    <div class="widget d-flex justify-content-center" id="task-tracker">
      <b-card>
          <Header @toggle="toggleNewTask" title="Task tracker" :showNewTask="showNewTask" />
          <div v-if="showNewTask">
            <AddTask @add-task="addTask" />
          </div>
          <Tasks @delete-item="deleteItem" :tasks="tasks" />
      </b-card>
    </div>

  </div>
</template>

<script>
import Header from './components/task-tracker/Header.vue'
import Tasks from './components/task-tracker/Tasks.vue'
import AddTask from './components/task-tracker/AddTask.vue'
import AddTodo from './components/todo/AddTodo.vue'
import Todos from './components/todo/Todos.vue'

export default {
  name: 'App',
  components: {
    Header,
    Tasks,
    AddTask,
    Todos,
    AddTodo
  },
  data() {
    return {
      tasks: [],
      todos: [],
      showNewTask: false,
      showNewTodo: false
    }
  },
  methods: {
    toggleNewTask() {
      this.showNewTask = !this.showNewTask
    },
    toggleNewTodo() {
      this.showNewTodo = !this.showNewTodo
    },
    addTask(task) {
      this.tasks = [...this.tasks, task]
    },
    addTodo(todo) {
      this.todos = [...this.todos, todo]
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
        day: '2021-03-10'
      } 
    ],
    this.todos = [
      {
        id: 1,
        text: 'Eat'
      },
      {
        id: 2,
        text: 'Sleep'
      }
    ]
  }
}
</script>

<style>
.nav {
  padding-left:  1rem !important;
  padding-right: 1rem !important;
}
.main-banner {
  padding-top: 2rem;
}
.widget {
  padding: 1rem;
  min-height: 80vh;
}
</style>
