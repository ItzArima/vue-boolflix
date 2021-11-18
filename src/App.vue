<template>
  <div class="container">
    <siteHeader />
    <siteMain />
    <siteFooter />
  </div>  
</template>

<script>
import siteHeader from './components/siteHeader.vue'
import siteMain from './components/siteMain.vue'
import siteFooter from './components/siteFooter.vue'

export default {
  name: 'App',
  components: {
    siteHeader,
    siteMain,
    siteFooter
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
