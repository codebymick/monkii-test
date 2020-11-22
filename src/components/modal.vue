<template>
  <div class="popup" @click="close">
    <div class="row">
      <div class="col-12 text-centered" v-for="(shirt, shirtIndex) in products" :key="shirtIndex">
        <div class="item" v-if="shirtId==shirt.id">
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
  },
  methods: {
    close() {
      this.$emit('close');
    }
  }
}
</script>

<style scoped>

</style>
