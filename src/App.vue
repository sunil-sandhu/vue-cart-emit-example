<template>
  <div id="app">


    <!-- Header component -->
    <section class="Header">
      <h1>Fruiticious!</h1>

      <!-- Cart component -->
      <div class="Cart">
        <p>Cart: {{this.cart.length}} items</p>
        <!-- Button component -->
        <Shop-Button-Empty-Cart
            @empty-cart="emptyCart">
          <p>Empty Cart</p>
        </Shop-Button-Empty-Cart>
        <p>Total: ${{this.total}}</p>
      </div>
    </section>


    <!-- Shop component -->
    <section class="Shop">
      <!-- Item component -->
      <shop-item v-for="item in this.items"
                 :item="item"
                 @update-cart="updateCart"
      >
      </shop-item>
    </section>


  </div>
</template>

<script>
import ShopItem from './components/Shop-Item.vue'
import ShopButton from './components/Shop-Button.vue'
import ShopButtonEmptyCart from './components/Shop-Button-Empty-Cart.vue'



import Banana from './assets/banana.jpg';
import Orange from './assets/orange.jpg';
import Apple from './assets/apple.jpg';
export default {
    name: 'app',
    components: {
      ShopItem, ShopButton, ShopButtonEmptyCart
    },
    data() {
        return {
            items: [
                {
                    id: 205,
                    name: 'Banana',
                    price: 1,
                    imageSrc: Banana
                },
                {
                    id: 148,
                    name: 'Orange',
                    price: 2,
                    imageSrc: Orange
                },
                {
                    id: 248,
                    name: 'Apple',
                    price: 1,
                    imageSrc: Apple
                }
            ],
            cart: [],
            total: 0
        }
    },
    computed: {
        shoppingCartTotal() {
            return this.total = this.cart.map(item => item.price).reduce((total, amount) => total + amount);
        }
    },
    methods: {
        updateCart(e) {
            this.cart.push(e);
            this.shoppingCartTotal;
        },

        emptyCart() {
            this.cart = [];
            this.total = 0;
        }
    },

}
</script>

<style>


body {
  margin: 20px auto;
  padding: 0;
  min-height: 100vh;
  max-width: 800px;
  background: linear-gradient(#ffd781, #ffc3c3);
  font-family: arial, sans-serif;
}


#app {
}

h1 {
  width: 100%;
  font-size: 3.5em;
  font-family: 'Lobster', cursive;
  font-weight: 300;
  color: yellow;
  text-align: center;

}


.Header {
  padding: 10px;
  width: auto;
  display: flex;
  /*border: 1px solid;*/
  background-color: red;
}

.Cart {
  /*border: 1px solid;*/
  border-radius: 5px;
  height: fit-content;
  background-color: white;
  text-align: center;
  font-size: 0.9em;
  padding: 5px;
}

.Button {
  /*border: 1px solid;*/
  width: 100px;
  height: 50px;
  border-radius: 5px;
  background: radial-gradient(#6bf88e, #5ce561);
  color: white;
  font-size: 14px;
  cursor: pointer;
}

.Shop {
  /*border: 1px solid;*/
}

.Item {
  /*border: 1px solid;*/
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 10px;
  background-color: white;
  border-bottom: 1px solid;
}

.ItemDetails {
}


.ItemImage {
  width: 150px;
  height: 150px;
  border: 1px dotted;
  border-radius: 5px;
}



@media screen and (max-width: 600px) {

  body {
    margin: 0 auto;
  }

  .ItemImage {
    width: 50px;
    height: 50px;
  }

  h1 {
    font-size: 2.5em;
    text-align: left;
  }
}

</style>
