<template>
  <div class="shopping-cart">
    <img v-if="loading" class="loading" src="@/assets/spinner.svg" alt="loading">
    <ProductList
      v-if="!loading"
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
      products: [],
      loading: true,
    };
  },
  beforeCreate() {
    productService.listShoppingCart()
      .then(((products) => {
        this.products = products;
        this.loading = false;
      }));
  },
  methods: {
    removeFromCart(product) {
      productService.removeFromShoppingCart(product)
        .then((oldProduct) => {
          console.log('product', oldProduct.name, 'was removed from shopping cart');
        });
    },
  },
};
</script>
