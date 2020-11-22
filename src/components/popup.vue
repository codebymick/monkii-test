<template>
  <div class="popup">
    <div class="row">
      <div class="col-12" v-for="(shirt, shirtIndex) in products" :key="shirtIndex">
        <div class="item">
          <div class="image-wrapper">
            <img :src="require('../assets/products/' + shirt.image)" :alt="shirt.name">
          </div>
          <div class="item-data">
            <div>{{shirtId}}</div>
            <div>{{shirt.name}}</div>
            <div>${{shirt.price}}</div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  import json from '../assets/json/products.json'

  export default {
  name: 'popup',
  data () {
    return {
      products: json.products
    }
  },
  props: {
    shirtId: Number
  }
}
</script>

<style scoped>

</style>
