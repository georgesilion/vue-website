<template>
    <div class="task">
        <h3>
            {{task.text}}
            <button @click="onDelete(task.id)" class="deleteButton">&#10008;</button>
        </h3>
        <p>{{task.day}}</p>
    </div>
</template>

<script>
export default {
    name: 'Task',
    props: {
        task: Object
    },
    methods: {
        onDelete(id) {
            this.$emit('delete-item', id)
        }
    }
}
</script>

<style scope>
.task {
    background: #f4f4f4;
    margin: 5px;
    padding: 1px;
    border-left: solid 6px;
    border-left-color: rgb(0, 189, 247);
    line-height: 0;
}
.deleteButton {
    background: tomato;
    border: none;
    color: white;
    cursor: pointer;
}
.deleteButton:hover {
    background: red;
}
</style>
