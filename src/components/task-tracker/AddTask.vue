<template>
    <b-container>
        <b-form @submit="onSubmit" name="add-form">
            <h4>Create new task</h4>
            <b-form-input type="text" v-model="text" name="text" placeholder="Task" class="user-input" required></b-form-input>
            <b-form-datepicker placeholder="Choose a date" type="text" v-model="day" name="day" :date-format-options="{ year: 'numeric', month: 'short', day: '2-digit'}" class="mb-2"></b-form-datepicker>
            <div class="text-center">
                <b-button block type="submit" variant="success">Save</b-button>
            </div>
        </b-form>
    </b-container>
</template>

<script>
export default {
    name: 'AddTask',
    data() {
        return {
            text: '',
            day: ''
        }
    },
    methods: {
        onSubmit(e) {
            e.preventDefault()
            const newTask = {
                id: Math.floor(Math.random() * 10000),
                text: this.text,
                day: this.day
            }
            this.$emit('add-task', newTask);
            this.text = ''
            this.day = ''
        }
    }
}
</script>

<style scoped>
form {
    background: #dad7d7;
    padding: 1px 10px 10px 10px;
    border-radius: 4px;
}
.user-input {
    margin-bottom: 0.2rem;
}
</style>