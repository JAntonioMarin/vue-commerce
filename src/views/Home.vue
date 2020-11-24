<template>
  <div class="home">
    <ProductList title="Products"
      button-text="Add to cart"
      @button-click="addToShoppingCart($event)"
      :products="products"
    />
  </div>
</template>

<script>
// @ is an alias to /src
import PRODUCTS from '@/utils/__mocks__/mock-products';
import SHOPPING_CART from '@/utils/__mocks__/mock-shopping-cart';
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
  methods: {
    addToShoppingCart(product) {
      console.log(product);
      SHOPPING_CART.push({ ...product });
    },
  },
};
</script>
