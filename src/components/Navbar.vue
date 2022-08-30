<template>
    <nav id="nav">
      <button
        class="btn fw-bold p-3 display-3"
        type="button"
        data-bs-toggle="offcanvas"
        data-bs-target="#staticBackdrop"
        aria-controls="staticBackdrop"
      >
        MENU
      </button>
      <div
        class="offcanvas offcanvas-start"
        data-bs-backdrop="static"
        tabindex="-1"
        id="staticBackdrop"
        aria-labelledby="staticBackdropLabel"
      >
        <div class="offcanvas-header">
          <h1 class="offcanvas-title fw-bold" id="staticBackdropLabel">
            Unlimited CMD
          </h1>
        </div>
        <div class="offcanvas-body">
          <div>
            <div class="row gap-2 d-flex justify-content-center fw-bold">
              <router-link to="/">Home <i class="bi bi-house"></i></router-link>
              <div v-if="user">
                <router-link to="/products">All Products<i class="bi bi-cart-fill"></i></router-link>
              </div>
              <div v-if="user">
                <router-link to="/admin">Admin <i class="bi bi-book"></i></router-link>
              </div>
              <router-link to="/login"
                >Login <i class="bi bi-person"></i
              ></router-link>
              <router-link to="/register"
                >Register <i class="bi bi-person-fill"></i
              ></router-link>
              <router-link to="/about"
                >About <i class="bi bi-book-fill"></i
              ></router-link>
          <div v-if="user">
            <button type="button" class="btn-new rounded border border-0" data-bs-target="#offcanvasScrolling" data-bs-toggle="offcanvas">Cart</button>
          </div>
            </div>
          </div>
        </div>
      </div>
    </nav>
  
    <CartVue />
  
  </template>
  
  <script>
  import CartVue from "./Cart.vue";
  export default {
    components: {CartVue},
      computed:{
        user(){
          return this.$store.state.user
        },
        cart(){
          return this.$store.state.cart
        }
      }
  }
  </script>
  
  <style scoped>
  
  </style>