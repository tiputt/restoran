<template>
  <div class="home">
    <Navbar />
    <!-- <div class="container"> -->
      <Banner/>
    <!-- </div> -->
    <div class="container">
      <div class="row mt-4">
        <div class="col">
          <h2>Best Product RestoranQu</h2>
        </div>
        <div class="col">
          <router-link to="/foods" class="btn btn-success float-right"><b-icon-eye></b-icon-eye> Semua</router-link>
        </div>
      </div>

      <div class="row mb-4">
        <div class="col-md-4 mt-4" v-for="product in products" :key="product.id">
          <CardProduct :product="product"/>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import Navbar from '@/components/Navbar.vue'
import Banner from '@/components/Banner.vue'
import CardProduct from '@/components/CardProduct.vue'
import axios from 'axios'

export default {
  name: 'Home',
  components: {
    Navbar,
    Banner,
    CardProduct,
  },
  data(){
    return {
      products: [],
    }
  },
  methods : {
    setProduct(data){
      this.products = data;
    }
  },
  mounted(){
    axios.get('http://localhost:4000/best-products')
      .then((response) => this.setProduct(response.data))
      .catch((error) => console.log(error))
  },
}
</script>
