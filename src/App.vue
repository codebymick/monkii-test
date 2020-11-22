<template>
  <Header/>
  <Products/>
</template>

<script>
  import Header from './components/header.vue'
  import Products from './components/products.vue'
  import('./assets/styles/style.css')

export default {
  name: 'App',
  components: {
    Products,
    Header
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /*text-align: center;*/
  color: #2c3e50;
}
</style>
