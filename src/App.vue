<template>
  <div id="app">
    <h1 class="ui dividing centered header">Example App</h1>
    <div class='ui three column centered grid'>
      <div class='column'>
        <product-list v-bind:products="products"></product-list>
        <create-product v-on:create-product="CreateProduct"></create-product>
      </div>
    </div>
  </div>
</template>

<script>
import sweetalert from 'sweetalert';
import ProductList from './components/ProductList';
import CreateProduct from './components/CreateProduct';

export default {
  name: 'app',
  components: {
    ProductList,
    CreateProduct,
  },
  data() {
    return {
      products: [{
        title: 'TV',
        description: '60-inch smart television',
        price: '$5,000',
        done: false,
      }, {
        title: 'Tennis',
        description: 'Vans brand tennis',
        price: '$1,000',
        done: true,
      }, {
        title: 'Cell Phone',
        description: 'Mid-range cell phone',
        price: '$3,500',
        done: false,
      }, {
        title: 'Ben & Frank lenses',
        description: 'Nice brand lenses "Ben & Frank"',
        price: '$1,800',
        done: false,
      }],
    };
  },
  methods: {
    CreateProduct(newProduct) {
      this.product.push(newProduct);
      sweetalert('Success!', 'Product created!', 'success');
    },
  },
};
</script>
