<template>
  <div class="genres-container">
      <div class="genre" v-for="element in namesOfGenre" :key="element.id">
          <div :class="element">

          </div>
      </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {

    data(){
        return {
            genres : [],
            array : this.genresArray,
        }
    },

    props:{
        genresArray : Array
    },

    mounted(){
        axios
            .get('https://api.themoviedb.org/3/genre/movie/list?api_key=80d8049aea831dd859481c955e96072b&language=en-US')
            .then(resp => {
                this.genres = resp.data.genres
                console.log(this.genres);
            })
            .catch(e=>{
                console.log(e)
            })     
    },

    computed:{
        namesOfGenre(){
            let genreName =[]
            for(let i=0;i<this.array.length;i++){
                for(let j=0;j<this.genres.length;j++){
                    if(this.array[i]==this.genres[j].id){
                        genreName.push(this.genres[j].name)
                    }
                }
            }
            return genreName
        }
    }
}
</script>

<style>

</style>