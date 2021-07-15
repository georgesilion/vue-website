<template>
    <header>
        <h1>
            {{ title }}
            <Button @button-click="$emit('toggle')" :text="showNewTask ? 'Close' : 'New task'" :color="showNewTask ? 'red' : 'green'"/>
        </h1>
    </header>
</template>

<script>
import Button from './Button.vue'

export default {
    name: 'Header',
    props: {
        title: String,
        showNewTask: Boolean
    },
    components: {
        Button
    }
}
</script>
