<template>
  <div class="container">
    <siteHeader @films ="films" @series="series" />
    <siteMain :selection="selection" :reset="reset" />
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
  },

  data(){
    return {
      selection : "films",
      elements : [],
      reset: 0,
    }
  },

  methods:{
    films(){
      this.selection = 'films'
      console.log(this.selection);
      this.reset = 1;
    },
    series(){
      this.selection = 'series'
      console.log(this.selection);
      this.reset = 1;
    },
  },

  computed:{

  }
}
</script>

<style lang="scss">
  @import "./assets/scss/common.scss";
  @import url('https://fonts.googleapis.com/css2?family=Genos:wght@200&display=swap');

</style>
