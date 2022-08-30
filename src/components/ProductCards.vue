<template>
    <div class="col-md-4 pb-5">
    <div class="product-card">
      <div class="badge ms-2">Sale</div>
        <div class="product-tumb">
          <img :src="product.img" alt="product"/>
        </div>
        <div class="product-details">
          <span class="product-catagory">Limited Edition</span>
          <h4> {{product.brand}} </h4>
          <div class="product-bottom-details d-flex justify-content-center">
            <div class="row">
              <div class="col-12">
                <div class="product-btns">
                  <router-link class="product-btn" :to="{name: 'singleProduct', params: {id: product.id}}"
                    ><span>details</span><i></i
                  ></router-link>
                </div>
              </div>
            </div>
          </div>
      </div>
    </div>
        </div>
</template>

<script>
export default {
  props: ['product']
}
</script>

<style>

</style>