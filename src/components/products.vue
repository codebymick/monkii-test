<template>
  <div class="products">
    <h2>Products</h2>
    <div class="status-line">
      <div class="item-count">{{displayedProducts.length}} items</div>
      <div class="filters">
          <label class="filter-label">Order by: </label>
          <select class="text-capitalize" v-model="selectedCat" size="1.5" @change="selectedCat!=selectedCat, changeOrder()">
            <option v-for="(ord, ordIndex) in category" :key="ordIndex" :value="ord" >{{ord}}</option>
          </select>

        <label class="filter-label">Filter by Size: </label>
        <select class="text-capitalize" v-model="selectedSize" size="1.5" @change="matchingSize(selectedSize)">
          <option v-for="(siz, sizIndex) in sizes" :key="sizIndex" :value="siz">{{siz}}</option>
        </select>
      </div>

    </div>
    <div class="container">
      <div class="row">
        <div class="col-sm-12 col-md-6 col-lg-4" v-for="(shirt, shirtIndex) in displayedProducts" :key="shirtIndex">
          <div class="item">
            <div class="image-wrapper">
              <img :src="require('../assets/products/' + shirt.image)" :alt="shirt.name">
            </div>
            <div class="item-data">
              <div>{{shirt.name}}</div>
              <div>${{shirt.price}}</div>
            </div>
          </div>
        </div>
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
        category: ['Price - Low to High', 'Price - High to Low'],
        selectedCat: 'Price - Low to High',
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
      },
      changeOrder() {
        if (this.selectedCat != 'Price - Low to High') {
          return this.displayedProducts.sort((a, b) => (a.price > b.price) ? -1 : 1);
        } else {
          return this.displayedProducts.sort((a, b) => (a.price < b.price) ? -1 : 1);
        }
      }
    },
    mounted() {
      this.displayedProducts = this.products
    }
  }
</script>

