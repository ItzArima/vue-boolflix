<template>
  <div class="vote-container">
      <div class="fullstar" >
          <img src="../assets/img/stars/star-solid.svg" alt="" v-for="yestar in stars" :key="yestar">
      </div>
      <div class="emptystar">
          <img src="../assets/img/stars/star-regular.svg" alt="" v-for="nostar in empty" :key="nostar">
      </div>
  </div>
</template>

<script>
export default {
    name :'votes',

    props :{
        vote : Number
    },

    methods:{
        pushStars(number){
            console.log(number);
        }
    },

    computed:{
        stars(){
            let x = this.vote / 2
            x =  Math.round(x)
            return x
        },
        empty(){
            let y = this.vote / 2
            y = 5 - Math.round(y)
            return y
        }
    }
}
</script>

<style>

</style>