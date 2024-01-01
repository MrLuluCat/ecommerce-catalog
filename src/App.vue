<template>
  <div>
    <button @click="fetchProducts">Next Product</button>
    <ItemProduct :product="currentProduct" />
  </div>
</template>

<script>
import axios from 'axios';
import ItemProduct from './components/ItemProduct.vue';

const API_URL = 'https://fakestoreapi.com/products/';

export default {
  components: {
    ItemProduct,
  },
  data() {
    return {
      currentProduct: null,
      currentIndex: 1,
    };
  },
  methods: {
    async fetchProducts() {
      try {
        const response = await axios.get(API_URL + this.currentIndex);
        const productData = response.data;

        if (
          productData.category === "men's clothing" ||
          productData.category === "women's clothing"
        ) {
          this.currentProduct = productData;
        } else {
          this.currentProduct = { title: 'Tidak Tersedia', category: 'Other' };
        }

        this.currentIndex = this.currentIndex === 20 ? 1 : this.currentIndex + 1;
      } catch (error) {
        console.error('Error fetching product:', error);
      }
    },
  },
};
</script>
