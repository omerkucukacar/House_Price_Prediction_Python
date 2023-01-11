<template>
  <div class="container">
    <div class="row">
      <div class="col-12 text-center">
        <h4 class="pt-3">My Properties</h4>

        <div class="container">
          <div class="row">
            <div class="col-12 text-left">
              <h2 class="pt-3"> Properties</h2>
            </div>
          </div>
          <div class="row">
            <div v-for="index in this.product_size" :key="index" class="col-md-6 col-xl-4 col-12 pt-3  justify-content-around d-flex">
              <ProductBox :product="products[index-1]">
              </ProductBox>
            </div>
          </div>
        </div>
        <router-link id="add-product" :to="{name : 'AddProduct'}" v-show="$route.name=='AdminProduct'">
          <button class="btn">Add a new Property</button>
        </router-link>
      </div>
    </div>
    <div class="row">
        <div v-for="product of products" :key="product.id" class="col-md-6 col-xl-4 col-12 pt-3  justify-content-around d-flex">
          <ProductBox :product="product">
          </ProductBox>
        </div>
    </div>
  </div>
</template>

<script>
import ProductBox from '../../components/Product/ProductBox';
export default {
  name: 'Product',
  components : {ProductBox},
  props : [ "baseURL" , "products" ],
  mounted(){
    if (this.$route.name=='AdminProduct' && !localStorage.getItem('token')) {
      this.$router.push({name : 'Signin'});
    }
  }
}
</script>

<script>
  import ProductBox from "../components/Product/ProductBox";
  import CategoryBox from "../components/Category/CategoryBox";
  export default {
    name: 'Home',
    components : { ProductBox, CategoryBox},
    props : ["baseURL", "products", "categories"],
    data(){
      return{
        category_size:0,
        product_size:0
      }
    },
    mounted(){
      this.category_size = this.categories.length;
      this.category_size = Math.min(6, this.category_size);

      this.product_size = this.products.length;
      this.product_size = Math.min(8, this.product_size);
    }
  }
</script>
<style scoped>
h4 {
  font-family: 'Roboto', sans-serif;
  color: #484848;
  font-weight: 700;
}

#add-product {
  float: right;
  font-weight: 500;
}
</style>
