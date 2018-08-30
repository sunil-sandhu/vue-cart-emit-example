<template>
    <button class="Button" @click="buttonClicked">
    <slot></slot>
    </button>
</template>

<script>

    export default {
        name: 'Shop-Button-Add',
        components: {},
        props: ['item'],
        data() {
            return {}
        },
        methods: {
            buttonClicked() {
                this.$emit('button-clicked')
            }
        }
    }
</script>

<style>

</style>
