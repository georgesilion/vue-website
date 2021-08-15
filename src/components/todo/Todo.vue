<template>
    <b-container>
        <div class="task">
            <b-form-checkbox v-model="status" name="checkbox-1" value="accepted" unchecked-value="not_accepted">
                <h3>
                    {{todo.text}}
                    <br>
                </h3>
            </b-form-checkbox>
        </div>
    </b-container>
</template>

<script>
export default {
    name: 'Todo',
    props: {
        todo: Object
    }
}
</script>

<style scope>

</style>
