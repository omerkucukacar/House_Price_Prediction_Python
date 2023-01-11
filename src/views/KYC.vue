<template>
  <div class="container">
    <!--    Logo Div-->
    <div class="row">
      <div class="col-12 text-center pt-3">
        <router-link :to="{ name: 'Home' }">
          <img id="logo" src="../assets/icon.png" />
        </router-link>
      </div>
    </div>

    <div class="row">
      <div class="col-12 justify-content-center d-flex flex-row pt-5">
        <div id="kyc-div" class="flex-item border">
          <h2 class="pt-4 pl-4">KYC Verification</h2>
          <h3 class="pt-4 pl-4">Thank you for your registration</h3>
          <p> We will forward you to our external partner for- you are in a quite and bright room the further identifcation process (KYC) </p>
          
          <form @submit="kyc" class="pt-4 pl-4 pr-4">
           
      
            <button type="submit" class="btn btn-primary mt-2 py-0">
             <a href="https://www.idnow.io/"> Continue with KYC-Verification></a>
            </button>
          </form>
          <hr />
        
          
          
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "KYC",
  props: ["baseURL"],
  
      
    
  }
  
      
</script>

<style scoped>
.btn-dark {
  background-color: #e7e9ec;
  color: #000;
  font-size: smaller;
  border-radius: 0;
  border-color: #adb1b8 #a2a6ac #a2a6ac;
}

.btn-primary {
  background-color: #f0c14b;
  color: black;
  border-color: #a88734 #9c7e31 #846a29;
  border-radius: 0;
}

#logo {
  width: 150px;
}

@media only screen and (min-width: 992px) {
  #signup-div {
    width: 40%;
  }
}
</style>
