<template>
    <b-container>
        <b-form @submit="onSubmit" name="add-form">
            <h4>Create new todo</h4>
            <b-form-input type="text" v-model="text" name="text" class="user-input" required></b-form-input>
            <div class="text-center">
                <b-button block type="submit" variant="success">Save</b-button>
            </div>
        </b-form>
    </b-container>
</template>

<script>
export default {
    name: 'AddTodo',
    data() {
        return {
            text: ''
        }
    },
    methods: {
        onSubmit(e) {
            e.preventDefault()
            const newTodo = {
                id: Math.floor(Math.random() * 10000),
                text: this.text,
            }
            this.$emit('add-todo', newTodo);
            this.text = ''
        }
    }
}
</script>