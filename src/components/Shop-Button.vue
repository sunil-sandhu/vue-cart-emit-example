<template>
    <button class="Button" @click="buttonClicked(item)">
    <slot></slot>
    </button>
</template>

<script>

    export default {
        name: 'Shop-Button',
        components: {},
        props: ['item'],
        data() {
            return {}
        },
        methods: {
            buttonClicked(item) {
                this.$emit('button-clicked', item)
            }
        }
    }
</script>

<style>

</style>
