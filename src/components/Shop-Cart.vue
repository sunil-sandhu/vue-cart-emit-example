<template>
    <div class="Cart">
        <p>Cart: {{this.cart.length}} items</p>
        <!-- Button component -->
        <Shop-Button-Empty
                @emit-empty-cart="emitEmptyCart">
            <p>Empty Cart</p>
        </Shop-Button-Empty>
        <p>Total: ${{this.total}}</p>
    </div>
</template>

<script>
import ShopButtonEmpty from './Shop-Button-Empty.vue'

    export default {
        name: 'Shop-Cart',
        components: {ShopButtonEmpty},
        props: ['cart', 'total'],
        data() {
            return {}
        },
        methods: {
            emitEmptyCart() {
                this.$emit('empty-cart')
            }
        }
    }
</script>

<style>

</style>
