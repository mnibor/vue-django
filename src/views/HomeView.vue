<template>
  <div>
    <!-- NAVIGATION -->
    <navigation-component-vue @getCategoryID="categoryID"></navigation-component-vue>

    <div class="mb-3" v-if="categoryReceived">
      <h3>Productos de la Categoría <strong>{{ categoryReceived }}</strong></h3>
      <button class="btn btn-lg btn-warning" @click="resetFilter">Mostrar todos los Productos</button>
      <div class="alert alert-warning mt-3" role="alert" v-if="filteredProducts.length === 0" >
        Lamentablemente no existen productos para la categoría <strong>{{ categoryReceived }}</strong>
      </div>
    </div>

    <div class="row row-cols-1 row-cols-md-3 g-4">
      <div class="col" v-for="product in filteredProducts" :key="product.id">
        <div class="card text-center">
          <img :src="product.image" class="card-img-top" alt="Imagen de {{ product.name }}">
          <div class="card-body">
            <h5 class="card-title">{{ product.name }}</h5>
            <h6 class="card-subtitle mb-2 text-body-secondary">{{ product.category_name }}</h6>
            <p class="card-text">{{ product.description }}</p>
          </div>
          <div class="card-footer text-danger">
            PRECIO: $ {{ product.price }} - Por {{ product.price_type_description }}
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  import axios from 'axios'
  import NavigationComponentVue from '../components/NavigationComponent.vue'

  export default {
    components: {
      NavigationComponentVue
    },

    name: 'HomeView',

    data() {
      return {
        products: [],
        filteredProducts: [],
        categoryReceived: null
      }
    },

    methods: {
      categoryID(categoryID, categoryName) {
        this.categoryReceived = categoryName
        if(categoryID) {
          this.filteredProducts = this.allProducts.filter((product) => product.category === categoryID)
        } else {
          this.filteredProducts = this.allProducts
        }
      },

      resetFilter() {
        this.categoryReceived = null
        this.filteredProducts = this.allProducts
      }
    },

    mounted() {
      axios.get('http://127.0.0.1:8000/api/products/')
      .then(response => {
        this.allProducts = response.data
        this.filteredProducts = this.allProducts
      })
      .catch(error => {
        console.log(error)
      })
    }
  }
</script>

<style>
  .card {
    border: 2px solid gray !important;
  }
</style>