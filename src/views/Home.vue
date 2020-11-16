<template>
  <div class="home">
    <ProductList title="Products" :products="products"/>
  </div>
</template>

<script>
// @ is an alias to /src
import PRODUCTS from '@/utils/__mocks__/mock-products';
import ProductList from '@/components/ProductList.vue';

export default {
  name: 'Home',
  components: {
    ProductList,
  },
  data() {
    return {
      products: PRODUCTS,
    };
  },
};
</script>
