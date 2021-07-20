<template>
    <div>
        <div :key="todo.id" v-for="todo in todos">
            <Todo :todo="todo" />
        </div>
    </div>
</template>

<script>
import Todo from './Todo.vue'

export default {
    name: 'Todos',
    props: {
        todos: Array
    },
    components: {
        Todo
    }
}
</script>