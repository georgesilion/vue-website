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
    padding: 1px 1px 1px 10px;
    border-left: rgb(32, 121, 148) solid 6px;
    line-height: 0.4;
}
.deleteButton {
    background: tomato;
    border: none;
    color: white;
    cursor: pointer;
    float: right;
    margin-right: 10px;
    padding: 2px 5px;
}
.deleteButton:hover {
    background: red;
}
</style>
