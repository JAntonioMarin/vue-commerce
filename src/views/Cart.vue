<template>
  <div class="cart">
    <ProductList title="Shopping Cart"/>
  </div>
</template>

<script>
// @ is an alias to /src
import ProductList from '@/components/ProductList.vue';

export default {
  name: 'Cart',
  components: {
    ProductList,
  },
};
</script>
