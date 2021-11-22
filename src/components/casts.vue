<template>
  <div class="casts-container">
      <div v-for="element in sliceCasts" :key="element.id" class="actor">
          <span>{{element.name}},</span>
      </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
    name : 'casts',
    data(){
        return{
            stApi : "",
            castsArray : [],
        }
    },

    props:{
        id : Number
    },

    mounted() {   
        this.stApi = 'https://api.themoviedb.org/3/movie/'+this.id+'/credits?api_key=80d8049aea831dd859481c955e96072b&language=en-US'  
        this.starringApi() 
    },

    methods:{
        starringApi(){
            axios
            .get(this.stApi)
            .then(resp => {
                this.castsArray = resp.data.cast
            })
            .catch(e=>{
                console.log(e)
            })  
        }
    },

    computed:{
        sliceCasts(){
            let cLength = this.castsArray.length
            return this.castsArray.slice(cLength - 5)
        }
    }
}
</script>
    
<style>

</style>