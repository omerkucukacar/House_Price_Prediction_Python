<template>
  <div class="container">
    <div class="row">
      <div class="col-12 text-center">
        <h4 class="pt-3">Tokenize My Property</h4>
      </div>
    </div>

    <div class="row">
      <div class="col-3"></div>
      <div class="col-md-6 px-5 px-md-0">
        <form>
          <div class="form-group">
            <label>Ad a New Property</label>
            <input type="text" class="form-control" v-model="product.title" required>
          </div>
        
          <div class="form-group">
            <label>Company (Seller)</label>
            <input type="text" class="form-control" v-model="product.company" required>
          </div> 
          
          <div class="form-group">
            <label>Category</label>
            <select class="form-control" v-model="categoryId" required>
              <option v-for="category of categories" :key="category.id" :value="category.id">{{category.categoryName}}</option>
            </select>
          </div>
          <div class="form-group">
            <label>ImageURL</label>
            <input type="url" class="form-control" v-model="imageURL" required>
          </div>
          <div class="form-group">
            <label>Area (m²)</label>
            <input type="number" class="form-control" v-model="product.area" required>
          </div>
            <div class="form-group">
              <label>Rooms</label>
              <input type="number" class="form-control" v-model="product.rooms" required>
            </div>
            <div class="form-group">
              <label>Bathrooms</label>
              <input type="number" class="form-control" v-model="product.bathrooms" required>
            </div>
            <div class="form-group">
              <label>Location</label>
              <input type="url" class="form-control" v-model="product.locaitons" required>
            </div>
          
          <div class="form-group">
            <label>Price for Tokens</label>
            <input type="number" class="form-control" v-model="price" required>
          </div>
          <button type="button" class="btn btn-primary" @click="addProduct">Save</button>
        </form>
      </div>
      <div class="col-3"></div>
    </div>
  </div>
</template>

<script>
export default {
  data(){
    return {
      id : null,
     title: null,
      company: null,
      area : null,
      rooms : null,
      bathrooms : null,
      locations:null,
      categoryId : null,
      name : null,
      description : null,
      imageURL : null,
      price : null
    }
  },
  props : ["baseURL", "products", "categories"],
  methods : {
    async addProduct() {
      const newProduct = {
        id : this.id,
        title: this.title,
        company: this.company,
        area : this.area,
        rooms : this.rooms,
        bathrooms : this.bathrooms,
        locations:this.locaitons,
        categoryId : this.categoryId,
        name : this.name,
        description : this.description,
        imageURL : this.imageURL,
        price : this.price
      }

      await axios({
        method: 'post',
        url: this.baseURL+"product/add",
        data : JSON.stringify(newProduct),
        headers: {
          'Content-Type': 'application/json'
        }
      })
      .then(res => {
        //sending the event to parent to handle
        this.$emit("fetchData");
        this.$router.push({name : 'AdminProduct'});
        swal({
          text: "Tokens Added Successfully!",
          icon: "success",
          closeOnClickOutside: false,
        });
      })
      .catch(err => console.log(err));
    }
  },
  mounted() {
    if (!localStorage.getItem('token')) {
      this.$router.push({name : 'Signin'});
    }
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
