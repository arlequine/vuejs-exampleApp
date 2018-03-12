<template>
  <div>
    <product v-on:delete-product="deleteProduct" v-on:incomplete-product="incompleteProduct" v-on:complete-product="completeProduct" v-for="product in products" :product.sync="product"></product>
  </div>
</template>

<script type = "text/javascript" >
import sweetalert from 'sweetalert';
import Product from './Product';

export default {
  props: ['products'],
  components: {
    Product,
  },
  methods: {
    deleteProduct(product) {
      sweetalert({
        title: 'Are you sure?',
        text: 'This Product will be permanently deleted!',
        type: 'warning',
        showCancelButton: true,
        confirmButtonColor: '#DD6B55',
        confirmButtonText: 'Yes, delete it!',
        closeOnConfirm: false,
      },
      () => {
        const productIndex = this.products.indexOf(product);
        this.products.splice(productIndex, 1);
        sweetalert('Deleted!', 'Your product has been deleted.', 'success');
      });
    },
    completeProduct(product) {
      const productIndex = this.products.indexOf(product);
      this.products[productIndex].done = true;
      sweetalert('Success!', 'Product on sale!', 'success');
    },
    incompleteProduct(product) {
      const productIndex = this.products.indexOf(product);
      this.products[productIndex].done = false;
      sweetalert('¡Out of sale!', 'Product not for sale', 'success');
    },
  },
};
</script>

<style scoped>
p.tasks {
  text-align: center;
}
</style>
