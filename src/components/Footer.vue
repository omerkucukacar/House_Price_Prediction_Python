<template>
  <footer>
    <div class="container pt-5">
      <div class="row">
        <div class="col-md-3 col-6">
          <ul style="list-style-type: none">
            <li><a class="footer-link font-weight-light" href="#">About Us</a></li>
            <li class="text-light font-weight-bold pb-2">Contact Us</li>
            <li><a class="footer-link font-weight-light" href="#">Help</a><br></li>
            
          </ul>
        </div>

        <div class="col-md-3 col-6">
          <ul style="list-style-type: none">

            <li><a class="footer-link font-weight-light" href="#">Facebook</a></li>
            <li><a class="footer-link font-weight-light" href="#">Twitter</a><br></li>
            <li><a class="footer-link font-weight-light" href="#">Instagram</a><br></li>
          </ul>
        </div>

      <div class="row">
        <div class="col-12">
          <div class="text-center py-5">
            <img id="logo" src="../assets/icon.png" />
          </div>
        </div>
      </div>
    </div> 
    </div>
    <h2>PRIVACY NOTE</h2>
    <br>
    <p>Generally the personal information we collect from you are for the purposes of dealing with your enquiry</p>
    <br>
    <h3>© 2022 REAL ESTATE - All rights reserved.</h3>
  </footer>
</template>

<script>
export default {
  name : "Footer"
}
</script>

<style>
footer {
  margin-top : 100px;
  background-color:#232F3E;
  font-size:16px;
}

li {
  padding-left: 0;
  padding-bottom: 10px;
}

a {
  text-decoration: none;
}

.footer-link {
  color: #DDD;
}

#logo {
  width: 150px;
}

footer {
  font-family: 'Roboto', sans-serif;
}


</style>
