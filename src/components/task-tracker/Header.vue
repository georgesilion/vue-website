<template>
    <b-container>
        <header>
            <h1>
                {{ title }}
                <Button @button-click="$emit('toggle')" :text="showNewTask ? 'Close' : 'New'" :class="showNewTask ? 'bg-danger' : 'bg-success'"/>
            </h1>
        </header>
    </b-container>
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
