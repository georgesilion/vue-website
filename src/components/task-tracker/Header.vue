<template>
    <b-container>
        <b-row>
            <b-col><h3>{{ title }}</h3></b-col>
            <b-col cols="4"><Button @button-click="$emit('toggle')" :text="showNewTask ? 'Close' : 'New'" :class="showNewTask ? 'bg-danger' : 'bg-success'"/></b-col>
        </b-row>
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
