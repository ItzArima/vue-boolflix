<template>
  <div class="container">
    <siteHeader @selection="typeSelection" />
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
      selection : "home",
      reset: 0,
    }
  },

  methods:{
    /* films(){
      this.selection = 'films'
      console.log(this.selection);
      this.reset = 0;
    },
    series(){
      this.selection = 'series'
      console.log(this.selection);
      this.reset = 0;
    }, */
    typeSelection(type){
      this.selection = type
    }
  },

  computed:{

  }
}
</script>

<style lang="scss">
  @import "./assets/scss/common.scss";
  @import url('https://fonts.googleapis.com/css2?family=Outfit:wght@500&display=swap');

</style>
