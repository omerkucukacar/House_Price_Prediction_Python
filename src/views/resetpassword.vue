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
          <div id="resetpassword-div" class="flex-item border">
            <h2 class="pt-4 pl-4">Reset password!</h2>
            <br>
            <p>We sent you a verifcation code. Please check your mails.</p>
            <br>
        
            <form @submit="resetpassword" class="pt-4 pl-4 pr-4">
                <div class="form-group">
                    <label>Code in your E-mail</label>
                    <input
                      type="number"
                      class="form-control"
                      v-model="code"
                      required
                    />
                  </div>
                  <br>

                <div class="form-group">
                    <label>New Password</label>
                    <input
                      type="password"
                      class="form-control"
                      v-model="password"
                      required
                    />
                  </div>
                  <br>

                  <div class="form-group">
                    <label>Repeat Password</label>
                    <input
                      type="password"
                      class="form-control"
                      v-model="password"
                      required
                    />
                  </div>
                  <br>

                  <button type="button" class="btn btn-primary" @click="resetpassword">Reset Password</button>

                <br>
                  <button type="button" class="btn btn-primary" @click="Signin">Continue to Log-In</button>
            </form>
            <hr />
            <small class="form-text text-muted pt-2 pl-4 text-center"
              >New to RealState?</small
            >
            <p class="text-center">
              <router-link
                :to="{ name: 'Signup' }"
                class="btn btn-dark text-center mx-auto px-5 py-1 mb-2"
                >Register</router-link
              >
            </p>
          </div>
        </div>
      </div>
    </div>
  </template>
  
  <script>
import Signin from './Signin.vue';

  export default {
    name: "forgotpassword",
    props: ["baseURL"],
    data() {
      return {
        email: null,
        password: null,
        loading: null,
      };
    },
    methods: {
      async signin(e) {
        e.preventDefault();
        this.loading = true;
  
        const user = {
          email: this.email,
          password: this.password,
        };
  
        await axios
          .post(`${this.baseURL}user/signIn`, user)
          .then((res) => {
            localStorage.setItem("token", res.data.token);
            this.$emit("fetchData");
            this.$router.push({ name: "Home" });
          })
          .catch((err) => {
            swal({
              text: "Your password has been reseted!",
              text: "You can now log in with your new password",
              icon: "error",
              closeOnClickOutside: false,
            });
            console.log(err);
          })
          .finally(() => {
            this.loading = false;
          });
      },
    },
    mounted() {
      this.loading = false;
    },
  };
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
    #signin-div {
      width: 40%;
    }
  }
  </style>