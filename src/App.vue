<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <div class="row">
      <div class="col-sm-1"></div>
      <div class="col-md-7">
        <div class="row">
          <div class="col-md-6" :key="product.id" v-for="product in products">
            <Product :isInCart="isInCart(product)" v-on:add-to-cart="addToCart(product)" :product="product"></Product>
          </div>
        </div>
      </div>
      <div class="col-md-3 my-5 sdbar">
        <Cart v-on:pay="pay()" v-on:remove-from-cart="removeFromCart($event)" :items="cart"></Cart>
      </div>
    </div>
  </div>
</template>

<script>
import products from './products.json'
import Product from './components/Products.vue'
import Cart from './components/Cart.vue'

export default {
  name: 'App',
  components: {
    Product,
    Cart
  },
  data(){
    return {
      products,
      cart: [],
    }
  },
  methods: {
    addToCart(product) {
      this.cart.push(product)
    },
    isInCart(product) {
      const item = this.cart.find(item => item.id === product.id)

      if(item) {
        return true
      } else{
        return false
      }
    },
    removeFromCart(product) {
      this.cart = this.cart.filter(item => item.id !== product.id)
    },
    pay() {
      this.cart = []
      alert('Purchase successful!')
    }
  },
}
</script>

<style>
body{
  background-color: #fbf8f3;
  text-align: center;
}
.sdbar{
  background-color: #d4d2cf;
}
</style>
