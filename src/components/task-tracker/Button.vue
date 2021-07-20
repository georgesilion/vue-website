<template>
    <b-button @click="onClick()" class="text-light">{{ text }}</b-button>
</template>

<script>
export default {
    name: 'Button',
    props: {
        text: String
    },
    methods: {
        onClick() {
            this.$emit('button-click')
        },
    }
}
</script>
