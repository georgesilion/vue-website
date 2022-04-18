<template>
  <div class="bg-secondary" id="top">

    <div class="top-nav">
        <b-navbar toggleable="sm" type="dark" variant="dark" class="nav" fixed="top">
          <b-navbar-brand href="#top">GS</b-navbar-brand>
          <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>
          <b-collapse id="nav-collapse" is-nav>
            <b-navbar-nav>
              <b-nav-item href="#todo">ToDo</b-nav-item>
              <b-nav-item href="#task-tracker">Task Tracker</b-nav-item>
              <b-nav-item href="#counter">Counter</b-nav-item>
            </b-navbar-nav>
          </b-collapse>
        </b-navbar>
    </div>

    <div class="text-light vh-100 d-flex align-items-center justify-content-center">
        <div class="text-center">
          <h1>Hello</h1>
          <b-button variant="outline-dark" href="#todo">Explore</b-button>
        </div>
    </div>

    <div class="vh-100 d-flex align-items-center justify-content-center" id="todo">
      <b-card>
        <Header @toggle="toggleNewTodo" title="To Do" :showNewTodo="showNewTodo" />
        <div v-if="showNewTodo">
          <AddTodo @add-todo="addTodo" />
        </div>
        <Todos :todos="todos"/>
      </b-card>
    </div>

    <div class="widget vh-100 d-flex align-items-center justify-content-center" id="task-tracker">
      <b-card>
          <Header @toggle="toggleNewTask" title="Task tracker" :showNewTask="showNewTask" />
          <div v-if="showNewTask">
            <AddTask @add-task="addTask" />
          </div>
          <Tasks @delete-item="deleteItem" :tasks="tasks" />
      </b-card>
    </div>

    <div class="vh-100 d-flex align-items-center justify-content-center text-center" id="counter">
      <b-card>
        <h1 class="inline-block"> {{counter}} </h1>
        <b-button class="p-4 m-2" variant="outline-warning" @click="decrement"><b>-</b></b-button>
        <b-button class="p-4 m-2" variant="outline-success" @click="increment"><b>+</b></b-button>
        <b-button class="px-5 m-3 d-block" variant="outline-danger" @click="reset">Reset</b-button>
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
      showNewTodo: false,
      counter: 0
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
    },
    increment() {
      this.counter += 1;
    },
    decrement() {
      if (this.counter <= 0)
        alert("Negative values not allowed!")
      else
        this.counter -= 1;
    },
    reset() {
      this.counter = 0;
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
.widget {
  padding: 1rem;
  min-height: 80vh;
}
</style>
