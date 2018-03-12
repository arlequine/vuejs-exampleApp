<template>
  <div class='ui centered card'>
    <div class="content" v-show="!isEditing">
      <div class='header'>
          {{ product.title }}
      </div>
      <div class='meta'>
          {{ product.description }}
      </div>
      <div class="meta">
        {{ product.price }}
      </div>
      <div class='extra content'>
          <span class='right floated edit icon' v-on:click="showForm">
          <i class='edit icon'></i>
        </span>
        <span class='right floated trash icon' v-on:click="deleteProduct(product)">
          <i class='trash icon'></i>
        </span>
      </div>
    </div>
    <div class="content" v-show="isEditing">
      <div class='ui form'>
        <div class='field'>
          <label>Title</label>
          <input type='text' v-model="product.title" >
        </div>
        <div class='field'>
          <label>Description</label>
          <input type='text' v-model="product.description" >
        </div>
        <div class='field'>
          <label>Price</label>
          <input type='text' v-model="product.price" >
        </div>
        <div class='ui two button attached buttons'>
          <button class='ui basic blue button' v-on:click="hideForm">
            Close X
          </button>
        </div>
      </div>
    </div>
    <div class='ui bottom attached green basic button' v-on:click="incompleteProduct(product)" v-show="!isEditing &&product.done">
        On Sale
    </div>
    <div class='ui bottom attached red basic button' v-on:click="completeProduct(product)" v-show="!isEditing && !product.done">
        Not for Sale
    </div>
  </div>
</template>

<script type="text/javascript">
  export default {
    props: ['product'],
    data() {
      return {
        isEditing: false,
      };
    },
    methods: {
      completeProduct(product) {
        this.$emit('complete-product', product);
      },
      incompleteProduct(product) {
        this.$emit('incomplete-product', product);
      },
      deleteProduct(product) {
        this.$emit('delete-product', product);
      },
      showForm() {
        this.isEditing = true;
      },
      hideForm() {
        this.isEditing = false;
      },
    },
  };
</script>
