<template>
  <div class="products">
    <h2>Products</h2>
    <div class="status-line">
      <div class="item-count">{{displayedProducts.length}} items</div>
<!--      <div>-->
<!--        <label class="filter-label">Order by: </label>-->
<!--        <select class="text-capitalize" v-model="showOrder" size="1.5">-->
<!--          <option v-for="(ord, ordIndex) in category" :key="ordIndex" :value="orderedBy" >{{ord}}</option>-->
<!--        </select>-->
<!--      </div>-->
      <div class="filters">
        <label class="filter-label">Filter by Size: </label>
        <select class="text-capitalize" v-model="selectedSize" size="1.5" @change="matchingSize(selectedSize)">
          <option v-for="(siz, sizIndex) in sizes" :key="sizIndex" :value="siz">{{siz}}</option>
        </select>
      </div>

    </div>
    <div class="container">
      <div class="item" v-for="(shirt, shirtIndex) in displayedProducts" :key="shirtIndex">
        <div class="image-wrapper">
          <img :src="require('../assets/products/' + shirt.image)" :alt="shirt.name">
        </div>
        <div>{{shirt.name}}</div>
        <div>${{shirt.price}}</div>
      </div>
    </div>
  </div>
</template>

<script>
  import json from '../assets/json/products.json'

  export default {
    name: 'Products',
    data() {
      return {
        products: json.products,
        category: ['Price - Low to High', 'Price - High to Low', 'Sleeve - Short to Long', 'Sleeve - Long to Short'],
        selectedCategory: '',
        sizes: ['All', 'S', 'M', 'L', 'XL'],
        selectedSize: 'All',
        displayedProducts: []
      }
    },
    methods: {
      matchingSize (el) {
        this.displayedProducts = []
        if (el == 'All') {
          this.displayedProducts = this.products
        } else {
          for(let i = 0; i < this.products.length; i++){
            for(let j = 0; j < this.products[i].sizes.length; j++){
              if(this.products[i].sizes[j] == el) {
                this.displayedProducts.push(this.products[i]);
              }
            }
          }
        }
      }
    },
    mounted() {
      this.displayedProducts = this.products
    }
  }
</script>

