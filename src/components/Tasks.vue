<template>
    <div>
        <div :key="task.id" v-for="task in tasks">
            <Item @delete-item="$emit('delete-item', task.id)" :task="task" />
        </div>
    </div>
</template>

<script>
import Item from './Item.vue'

export default {
    name: 'Tasks',
    props: {
        tasks: Array
    },
    components: {
        Item
    }
}
</script>