<template>
    <b-container>
        <div class="task">
            <h3>
                <div style="float: left">
                    {{task.text}}
                </div>
                <b-button @click="onDelete(task.id)" variant="danger" class="text-light deleteButton">
                    &#10008;
                </b-button><br>
            </h3>
            <h6>
                {{task.day}}
            </h6>
        </div>
    </b-container>
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
    background: #dad7d7;
    margin-top: 0.5rem;
    padding: 1px 1px 1px 10px;
    border-left: rgb(32, 121, 148) solid 6px;
    line-height: 0.4;
    border-radius: 4px;
}
.deleteButton {
    margin: 10px;
    float: right;
}
</style>
