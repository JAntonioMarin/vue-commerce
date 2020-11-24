<template>
  <div class="shopping-cart">
    <ProductList
      title="Shopping Cart"
      :products="products"
      button-text="remove from cart"
      @button-click="removeFromCart($event)"
    />
  </div>
</template>

<script>
// @ is an alias to /src
import ProductList from '@/components/ProductList.vue';
import * as productService from '@/product-service';

export default {
  name: 'ShoppingCart',
  components: {
    ProductList,
  },
  data() {
    return {
      products: productService.listShoppingCart(),
    };
  },
  methods: {
    removeFromCart(product) {
      productService.removeFromShoppingCart(product);
    },
  },
};
</script>
