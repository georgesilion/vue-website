<template>
    <form @submit="onSumbit" name="add-form">
        <div>
            <label>Task</label>
            <input type="text" v-model="text" name="text"/>
        </div>
        <div>
            <label>Day and Time</label>
            <input type="text" v-model="day" name="day"/><br><br>
        </div>
        <input type="submit" value="Save" >
    </form>
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
        onSumbit(e) {
            e.preventDefault()
            if(!this.text) {
                alert('Please add text')
                return
            }
            const newTask = {
                id: Math.floor(Math.random() * 100000),
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
input[type=text] {
  width: 100%;
  padding: 12px 20px;
  display: inline-block;
  border: 1px solid #ccc;
  box-sizing: border-box;
}
input[type=submit] {
  width: 100%;
  background-color: green;
  color: white;
  padding: 14px 20px;
  border: none;
  cursor: pointer;
}
input[type=submit]:hover {
    background-color: rgb(122, 167, 98)
}
form {
    background: rgb(180, 180, 175);
    padding: 10px;
}
</style>