<template>
  <div id="app">


    <!-- Header component -->
    <section class="Header">
      <h1>Fruiticious!</h1>

      <!-- Cart component -->
      <div class="Cart">
        <p>Cart (0)</p>
        <!-- Button component -->
        <Shop-Button><p>Empty Cart</p></Shop-Button>
      </div>
    </section>


    <!-- Shop component -->
    <section class="Shop">
      <!-- Item component -->
      <shop-item v-for="item in this.items"
                 :item="item"
      >
      </shop-item>
    </section>


  </div>
</template>

<script>
import ShopItem from './components/Shop-Item.vue'
import ShopButton from './components/Shop-Button.vue'



import Banana from './assets/banana.jpg';
import Orange from './assets/orange.jpg';
import Apple from './assets/apple.jpg';
export default {
    name: 'app',
    components: {
      ShopItem, ShopButton
    },
    data() {
        return {
            items: [
                {
                    id: 205,
                    name: 'Banana',
                    price: 50,
                    imageSrc: Banana
                },
                {
                    id: 148,
                    name: 'Orange',
                    price: 60,
                    imageSrc: Orange
                },
                {
                    id: 248,
                    name: 'Apple',
                    price: 40,
                    imageSrc: Apple
                }
            ],
            cart: []
        }
    }
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
