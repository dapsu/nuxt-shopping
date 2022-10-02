<template>
  <div class="app">
    <main>
      <div>
        <input type="text">
      </div>
      <ProductList></ProductList>
    </main>
  </div>
</template>

<script>
// import axios from 'axios';
import ProductList from '~/components/ProductList.vue';
export default {
  components: { ProductList },
  // async aysncData() {
  //   const response = await axios.get('http://localhost:3000/products');
  //   const products = response.data;
  //   return { products };
  // },
}
</script>

<style scoped>
  .flex {
    display: flex;
    justify-content: center;
  }
  .item {
    display: inline-block;
    width: 400px;
    height: 300px;
    text-align: center;
    margin: 0 0.5rem;
    cursor: pointer;
  }
  .product-image {
    width: 400px;
    height: 250px;
  }
  .app {
    position: relative;
  }
  .cart-wrapper {
    position: sticky;
    float: right;
    bottom: 50px;
    right: 50px;
  }
  .cart-wrapper .btn {
    display: inline-block;
    height: 40px;
    font-size: 1rem;
    font-weight: 500;
  }
</style>