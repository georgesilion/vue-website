<template>
    <header>
        <h1>
            {{ title }}
            <Button @toggle="$emit('toggle')" text="Create task" color="green"/>
        </h1>
    </header>
</template>

<script>
import Button from './Button.vue'

export default {
    name: 'Header',
    props: {
        title: String,
    },
    components: {
        Button
    }
}
</script>
