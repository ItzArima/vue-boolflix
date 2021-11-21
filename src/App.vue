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
    typeSelection(type){
      this.selection = type
      window.scrollTo(0,0)
    }
  },

  computed:{

  }
}
</script>

<style lang="scss">
  @import "./assets/scss/common.scss";
  @import url('https://fonts.googleapis.com/css2?family=Outfit:wght@100&display=swap');
  @import url('https://fonts.googleapis.com/css2?family=Kanit:wght@100&display=swap');

</style>
