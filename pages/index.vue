<template>
  <div class="app">
    <main>
      <div>
        <SearchInput v-model="inputText" @search="filterItemsBySearchText"></SearchInput>
        <!-- :search-keyword="searchKeyword" @input="updateSearchKeyword" == v-model="searchKeyword" -->
        <ul>
          <li v-for="item in items" :key="item.id" class="item flex" @click="moveToDetailPage(item.id)">
            <img class="product-image" :src="item.imageUrl" alt="product.name" />
            <p>{{ item.name }}</p>
            <span>{{ item.price }}</span>
          </li>
        </ul>
      </div>
    </main>
  </div>
</template>

<script>
// import axios from 'axios';
import SearchInput from '~/components/SearchInput.vue';
import { fetchProducts, fetchProductsByKeyword } from '@/api/index'

export default {
  components: { SearchInput },
  async asyncData() {
    try {
      const { data } = await fetchProducts();
      const items = data.map((item) => ({
        ...item,
        imageUrl: `${item.imageUrl}?random=${Math.random()}`,
      }));
      return { items };
    } catch (error) {
      const items = [];
      return { items };
    }
  },
  data() {
    return {
      inputText: "",
    }
  },
  methods: {
    moveToDetailPage(id) {
      // console.log(id);
      this.$router.push(`detail/${id}`);
    },
    // updateSearchKeyword(keyword) {
    //   this.searchKeyword = keyword;
    // },
    async filterItemsBySearchText() {
      const { data } = await fetchProductsByKeyword(this.inputText)
      this.items = data.map((item) => ({
        ...item,
        imageUrl: `${item.imageUrl}?random=${Math.random()}`,
      }));
    },
  },
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