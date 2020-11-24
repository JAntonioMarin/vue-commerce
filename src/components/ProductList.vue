<template>
  <div class="wrapper">
    <h1>{{title}}</h1>
    <div class="views">
      <span v-on:click="gridActive=false"  class="material-icons" :class="{selected:!gridActive}">
        view_list
      </span>
      <span v-on:click="gridActive=true"  class="material-icons" :class="{selected:gridActive}">
        view_module
      </span>
    </div>
    <ul v-bind:class="{ grid: gridActive  }">
      <li v-for="(product, index) in products" :key="index">
        <h2>{{ product.name }}</h2>
        <img :src="product.image" :alt="product.name">
        <p>
          {{shortDescription(product.description, 150)}}
        </p>
        <div class="price">{{ product.price | currency }}</div>
        <div>
          <button class="button" @click="$emit('button-click', product)">{{ buttonText }}</button>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
// import PRODUCTS from '@/utils/__mocks__/mock-products';

export default {
  name: 'ProductList',
  data() {
    return {
      gridActive: false,
      // products: PRODUCTS,
    };
  },
  props: {
    products: {
      id: String,
      name: String,
      price: Number,
      description: String,
      image: String,
      createAt: String,
    },
    title: String,
    buttonText: String,
  },
  filters: {
    currency(value) {
      return value.toLocaleString('es-ES', {
        style: 'currency',
        currency: 'EUR',
        currencyDisplay: 'symbol',
      });
    },
  },
  methods: {
    print() {
      console.log('Escribeee');
    },
    shortDescription(text, size) {
      return text.length > size ? `${text.slice(0, size)}...` : text;
    },
  },
  mounted() {
    console.log('Product mounted');
  },
};
</script>

<style scoped>
.views {
  margin: 10px 0;
}
.views span {
  margin-right: 5px;
}
ul {
  margin: 0;
  padding: 0;
  list-style: none;
  display: grid;
  grid-gap: 10px;
}
ul li {
  display: grid;
  grid-gap: 10px;
  grid-template-columns: minmax(100px, 150px) auto;
  grid-template-areas: "a b"
                       "a c"
                       "a d"
                       "a e";
  border-bottom: 2px solid lightgray;
  padding-bottom: 20px;
}
ul li * {
  margin: 0;
}
ul li h2 {
  grid-area: b;
  font-size: 14px;
}
ul li img {
  grid-area: a;
  display: block;
  width: 100%;
  max-width: 150px;
}
ul li .price {
  font-size: 16px;
  font-weight: bold;
}

/*grid view*/
ul.grid {
  grid-template-columns: repeat(auto-fit, minmax(130px, 1fr));
}

ul.grid li {
  display: block;
  padding-bottom: 0;
  border-bottom: none;
}

ul.grid li img {
  max-width: none;
}

ul.grid li p {
  display: none;
}

.views .selected {
  border: 1px solid darkgray;
  background: lightgrey;
}

</style>
