<template>
    <div class="Item">
        <img :src="item.imageSrc" :alt="item.name" class="ItemImage">
        <div class="ItemDetails">
            <p>Product: <strong>{{item.name}}</strong></p>
            <p>Price: <strong>${{item.price}}</strong></p>
        </div>
        <!-- Button component -->
        <Shop-Button
                @button-clicked="addToCart(item)"
                :item="item">
            <p>Add To Cart</p>
        </Shop-Button>
    </div>
</template>

<script>
import ShopButton from './Shop-Button.vue'

    export default {
        name: 'Shop-Item',
        components: { ShopButton },
        props: ['item'],
        data() {
            return {}
        },

        methods: {
            addToCart(item) {
                this.$emit('update-cart', item)
            }
        }
    }
</script>

<style>

</style>
