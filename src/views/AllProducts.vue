<template>
    <div class="allProducts pb-5 pt-5">
      <div class="container">
        <h2 class="display-2">Products</h2>
        <div class="row" v-if="products">
          <input type="search" class="rounded h-50" name="search" id="search" placeholder="Please Search for Name of Product" v-model="search">
            <ProductCards v-for="product in products" :key="product" :product="product" />
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
  import ProductCards from "../components/ProductCards.vue";
  export default {
    components:{ProductCards},
    data(){
      return{
        search: ''
      }
    },
    mounted() {
      this.$store.dispatch("getProducts");
    },
    computed: {
      products() {
        return this.$store.state.products?.filter(products =>{
            let isMatch = true;
            if (!products.title.toLowerCase().includes(this.search.toLowerCase())) {
                isMatch = false;
            }
            return isMatch
            })
          }
    },
  };
  </script>
  <style scoped>
  
  </style>