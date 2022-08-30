<template>
    <div class="singleProduct d-flex justify-content-center pb-5 pt-5">
      <div class="container">
        <router-link to="/products"><button class="btn btn-new">Back</button></router-link>
      <div class="product-card" v-if="product">
          <div class="product-tumb">
              <img class="img-fluid" :src="product[0].img" alt="product">
          </div>
          <div class="product-details">
              <span class="product-catagory">{{product[0].category}}</span>
              <h4><a href="">{{product[0].brand}}</a></h4>
              <p>{{product[0].description}}</p>
              <div class="product-bottom-details">
                  <div class="row">
                      <div class="col-12">
                          <div class="product-price ps-5">R{{product[0].price}}</div>
                      </div>
                  </div>
                  <div class="row">
                    <div class="col-12">
                        <div class="product-btns" @click="addCart()">
                          <a class="product-btn" target="_blank"><span>Add to cart</span><i></i></a>
                                </div>
                    </div>
                  </div>
              </div>
          </div>
      </div>
    <div v-else id="loading">
        <div class="loader">
          <div class="loaderBar"></div>
        </div>
    </div>
      </div>
  </div>
  </template>
  
  <script>
  export default {
    props: ['id'],
      mounted() {
      this.$store.dispatch("getProduct", this.id);
      },
      computed: {
        product() {
          return this.$store.state.product;
        },
        user(){
          return this.$store.state.user
        }
      },
      methods:{
        addCart(){
          let product = {
            brand: this.product[0].brand,
            category: this.product[0].category,
            description: this.product[0].description,
            img: this.product[0].img,
            price: this.product[0].price
            // created_by: this.product[0].created_by
          }
          this.$store.dispatch('addCart', product, this.user.id)
        }
      }
  }
  </script>
  
  <style scoped>
  
  </style>
