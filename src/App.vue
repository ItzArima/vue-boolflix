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
  @import "./assets/scss/common.scss";
  @import url('https://fonts.googleapis.com/css2?family=Genos:wght@200&display=swap');

</style>
