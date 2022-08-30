<template>
    <div
      class="login d-flex justify-content-center align-items-center flex-column"
    >
      <div
        class="container d-flex justify-content-center align-items-center flex-column"
      >
        <h3 class="display-4">Login</h3>
        <div class="form pb-3">
          <div class="row">
            <div class="col-12 fw-bold">
              <h4><label for="email">Email:</label></h4>
            </div>
            <div class="col-12">
              <input
                name="email"
                type="email"
                placeHolder="Enter your Email"
                class="form-control w-100 mx-auto"
                v-model="email"
              />
            </div>
          </div>
          <div class="row">
            <div class="col-12">
              <h4><label for="password">Password:</label></h4>
            </div>
            <div class="col-12">
              <input
                name="password"
                type="password"
                placeHolder="Enter your Password"
                class="form-control w-100 mx-auto"
                v-model="password"
              />
            </div>
          </div>
          <div class="col-12 pt-3">
            <button class="btn border border-0" type="button" @click="login()">Login</button>
          </div>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
      data(){
        return{
            email: '',
            password: '',
        }
      },
      methods:{
        login(){
          const user = {
              email: this.email,
              password: this.password
          }
        this.$store.dispatch('login', user) 
        }
      }
  };
  </script>
  
  <style scoped>
  
  </style>