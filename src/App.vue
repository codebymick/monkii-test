<template>
  <Header/>
  <Products/>
  <Footer/>
</template>

<script>
  import Header from './components/header.vue'
  import Products from './components/products.vue'
  import Footer from './components/footer.vue'
  import('./assets/styles/style.css')

export default {
  name: 'App',
  components: {
    Products,
    Header,
    Footer
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
