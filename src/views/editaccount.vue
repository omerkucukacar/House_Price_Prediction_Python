<template>
    <div class="container">
      <div class="row">
        <div class="col-12 text-center">
          <h4 class="pt-3">Edit My Account</h4>
        </div>
      </div>
  
      <div class="row">
        <div class="col-3"></div>
        <div class="col-md-6 px-5 px-md-0">
          <form v-if="product">
            <div class="form-group">
              <label>First Name</label>
              <select class="form-control" v-model="product.categoryId" required>
                <option v-for="category of categories" :key="category.id" :value="category.id">{{category.categoryName}}</option>
              </select>
            </div>
            <div class="form-group">
              <label>Last Name</label>
              <input type="text" class="form-control" v-model="product.title" required>
            </div>
            <div class="form-group">
              <label>E-mail</label>
              <input type="text" class="form-control" v-model="product.company" required>
            </div>
            <div class="form-group">
              <label>Password</label>
              <input type="password" class="form-control" v-model="product.imageURL" required>
            </div>
            <div class="form-group">
              <label> Mobile Number</label>
              <input type="number" class="form-control" v-model="product.name" required>
            </div>
            <div class="form-group">
              <label>Company</label>
              <input type="number" class="form-control" v-model="product.name" required>
            </div>
          </form>
        <router-link id="add-image" :to="{name : 'AddImage'}">
          <button class="btn">Add a new Image</button>
        </router-link>

        <label for="myfile">Select image :</label>
        <input type="file" id="myfile" class="form-control-file" @change="onFileSelected">
      </div>
      <button type="button" class="btn btn-info" @click="onUpload">Upload</button>

    <div class="row">
      <div v-for="image of images" :key="image.name" class="col-md-6 col-xl-4 col-12 pt-3  justify-content-around d-flex">
        <ImageBox :image="image"></ImageBox>
      </div>
    </div>
            
            <button type="button" class="btn btn-primary" @click="editProduct">Save</button>
          
        
        <div class="col-3"></div>
      </div>
    </div>

  </template>
  
  <script>
  export default {
    data(){
      return {
        product: null,
        selectedFile : null
      }
    },
    props : ["baseURL", "products", "categories"],
    methods : {
      async editProduct() {
        axios.post(this.baseURL+"product/update/"+this.id, this.product)
        .then(res => {
          //sending the event to parent to handle
          this.$emit("fetchData");
          this.$router.push({name : 'AdminProduct'});
          swal({
            text: "Properties Updated Successfully!",
            icon: "success",
            closeOnClickOutside: false,
          });
        })
        .catch(err => console.log("err", err));
      }
    },
    onFileSelected(event){
            //this will always update the selected file whenever user changes files
            this.selectedFile = event.target.files[0];
        },
        async onUpload(){
            if(!this.selectedFile) {
                swal({
                    text: "Select a file first",
                    icon: "warning",
                    closeOnClickOutside: false,
                });
                return;
            }
            if(this.selectedFile.type !== "image/jpeg" && this.selectedFile.type !== "image/png" &&
               this.selectedFile.type !== "image/jpg") {
                //file format is not correct
                swal({
                    text: "Select a image/jpeg file!",
                    icon: "error",
                    closeOnClickOutside: false,
                });
                return;
            }
            const formData = new FormData();
            formData.append('file', this.selectedFile);

            await axios({
                method: 'post',
                url: this.baseURL + "fileUpload/",
                data : formData,
            })
            .then(res => {
                this.$router.push({name : "Gallery"});
                swal({
                    text: "Image Added Successfully!",
                    icon: "success",
                    closeOnClickOutside: false,
                });
            })
            .catch(err => console.log(err))
        },
    


    mounted() {
      if (!localStorage.getItem('token')) {
        this.$router.push({name : 'Signin'});
        return;
      }
      this.id = this.$route.params.id;
      this.product = this.products.find(product => product.id == this.id);

    }
}




    

    
  </script>
  
  <style scoped>
  h4 {
    font-family: 'Roboto', sans-serif;
    color: #484848;
    font-weight: 700;
  }
  
  </style>
  