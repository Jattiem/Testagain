<template>
    <div class="cart" v-if="user">
      <div class="offcanvas offcanvas-end" data-bs-scroll="true" data-bs-backdrop="true" tabindex="-1" id="offcanvasScrolling">
    <div class="offcanvas-header">
      <h1 class="offcanvas-title" id="offcanvasScrollingLabel">Cart<i class="bi bi-cart-fill"></i></h1>
      <button type="button" class="btn-close" data-bs-dismiss="offcanvas"></button>
    </div>
    <div class="offcanvas-body">
      <p>{{user.fullname}}'s Cart </p>
      <div v-if="cart" id="cart">
        <div id="card" v-for="product in cart" :key="product" :product="product">
            <img :src="product.image" alt="Cart Item" class="img-fluid">
            <h3>{{product.brand}}</h3>
            <h5>R{{product.price}}</h5>
        </div>
        <div id="total">
          <h2>R{{total}}</h2>
        </div>
      </div>
      <div v-else>
          <h3>No Items in Cart</h3>
      </div>
    </div>
    <div class="offcanvas-footer">
      <button type="button" id="clearButton" @click="clear()">Checkout</button>
    </div>
  </div>
    </div>
  </template>
  
  <script>
  import ProductCards from '../components/ProductCards.vue'
  export default {
    components:{ProductCards},
      computed:{
        user(){
          return this.$store.state.user
        },
        cart(){
          return this.$store.state.cart
        },
        total(){
          return Math.round((this.$store.state.total + Number.EPSILON)*100)/100
        }
      },
      methods:{
        clear(){
          this.$store.dispatch('deleteCart')
          this.cart = null
        }
      }
  }
  </script>
  
  <style scoped>

  </style>