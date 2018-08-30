<template>
  <div id="app">



    <section class="Header">

      <h1>Fruiticious!</h1>

      <!-- Cart component -->
      <shop-cart
          :cart="this.cart"
          :total="this.total"
          @empty-cart="emptyCart">

      </shop-cart>

    </section>



      <!-- Item component -->
      <shop-item v-for="item in this.items"
                 :item="item"
                 :key="item.id"
                 @update-cart="updateCart"
      >
      </shop-item>


  </div>
</template>

<script>
import ShopCart from './components/Shop-Cart.vue'
import ShopItem from './components/Shop-Item.vue'
import ShopButton from './components/Shop-Button-Add.vue'
import ShopButtonEmpty from './components/Shop-Button-Empty.vue'



import Banana from './assets/banana.jpg';
import Orange from './assets/orange.jpg';
import Apple from './assets/apple.jpg';
export default {
    name: 'app',
    components: {
      ShopCart, ShopItem, ShopButton, ShopButtonEmpty
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
            return this.cart.map(item => item.price).reduce((total, amount) => total + amount);
        }
    },
    methods: {
        updateCart(e) {
            this.cart.push(e);
            this.total = this.shoppingCartTotal;
        },

        emptyCart() {
            this.cart = [];
            this.total = 0;
        }
    },

}
</script>

<style lang="scss">


body {
  margin: 20px auto;
  padding: 0;
  min-height: 100vh;
  max-width: 800px;
  background: linear-gradient(#fcac00, #b60000);
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
  background: linear-gradient(#ae0220, red);
  border-top-left-radius: 10px;
  border-top-right-radius: 10px;
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
  width: 120px;
  height: 60px;
  border-radius: 5px;
  background: radial-gradient(#6bf88e, #5ce561);
  color: white;
  font-size: 14px;
  cursor: pointer;
  p {
    color: #3c3c3c;
    font-weight: bold;
  }
}


.Item {
  /*border: 1px solid;*/
  display: flex;
  /*justify-content: space-between;*/
  align-items: center;
  padding: 10px;
  background-color: white;
  border-bottom: 1px dotted;
}

.ItemDetails {
  flex-grow: 0.9;
  padding-left: 20px;
}


.ItemImage {
  width: 150px;
  height: 150px;
  /*border: 1px dotted;*/
  /*border-radius: 5px;*/
}



@media screen and (max-width: 600px) {

  body {
    margin: 0 auto;
  }

  .Header {
    border-top-left-radius: 0;
    border-top-right-radius: 0;
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
