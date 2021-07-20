<template>
    <b-container>
        <div class="task">
            <h3>
                {{todo.text}}
                <br>
            </h3>
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
