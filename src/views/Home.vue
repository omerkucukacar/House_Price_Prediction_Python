<template>
  <div id="home">
    <!-- Page Wrapper -->
    <div id="background-div" class="page-holder bg-cover">

      <div class="container py-5">
        <header class="text-left text-white py-5">
          <h3 class="mb-4 rounded"><a href="C:\Users\ben\Desktop\RealEstate-master\ecommerce-vuejs-master\src\views\Signup.vue" class="bg-white px-2 py-2 rounded" id="heading">Register</a></h3>
          <br>
          <h3 class="mb-4 rounded"><a href="C:\Users\ben\Desktop\RealEstate-master\ecommerce-vuejs-master\src\views\Signin.vue" class="bg-white px-2 py-2 rounded" id="heading">Log-In</a></h3>
          <p id="content" class="lead mb-0 bg-dark p-1 rounded"></p>
        </header>
      </div>
    </div>


    <hr>
  </div>
</template>

<script>
  export default {
    name: 'Home',
    props : ["baseURL",],
    data(){
      return{
        category_size:0,
        product_size:0
      }
    }
  }
    
</script>

<style>
  .page-holder {
    min-height: 100vh;
  }

  .bg-cover {
    background-size: cover !important;
  }

  #background-div {
    background: url(../assets/home.png)
  }

  #heading {
    text-decoration: none;
    font-family: 'Roboto', sans-serif;
    font-weight: 400;
    opacity: 0.8;
    font-family: 'Josefin Sans', sans-serif;
  }

  #content {
    opacity: 0.8;
  }

  h2 {
    font-family: 'Josefin Sans', sans-serif;
  }
</style>
