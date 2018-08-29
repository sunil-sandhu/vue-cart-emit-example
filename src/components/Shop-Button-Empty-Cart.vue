<template>
    <button class="Button" @click="buttonClicked">
        <slot></slot>
    </button>
</template>

<script>

    export default {
        name: 'Shop-Button-Empty-Cart',
        components: {},
        data() {
            return {}
        },
        methods: {
            buttonClicked() {
                this.$emit('empty-cart')
            }
        }
    }
</script>

<style>

</style>
