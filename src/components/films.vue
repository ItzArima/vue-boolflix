<template>
    <div class="films-container">
        <search @runApi="getApi" :selection="this.selection"/>
        <div v-if="resett == 0" class="results-container">
            <div v-for="film in elements" :key="film.id" class="film">
                <div  class="img-container"> 
                    <div v-if="film.poster_path != null" class="image-verifier">   
                        <img :src="'https://image.tmdb.org/t/p/w300'+film.poster_path" alt="" srcset="">
                    </div>    
                    <div v-else class="image-verifier">
                        <h1>No Image</h1>
                    </div>
                </div>
                <h2>{{film.title}}</h2>
                <div class="original-title-container">
                    <p>Original title -</p>
                    <p> > {{film.original_title}}</p>
                </div>
                <div class="language-container">
                    <p>Original language -</p>
                    <p> > {{film.original_language}}</p>
                    <img :src="require(`../assets/img/flags/${film.original_language}.png`)" alt="">
                </div>
                <div class="vote-container">
                    <p>Vote -</p>
                    <p> > {{film.vote_average}}</p>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import axios from 'axios'
import search from './search.vue'

export default {
    name : 'films',

    components :{
        search,
    },

    props:{
        selection : String,
        reset : Number
    },

    data(){
        return{
            elements : [],
            myApi : '',
            resetElement : this.reset
        }
    },

    methods :{
        launchApi(){
            axios
                .get(this.myApi)
                .then(r => {
                    console.log(r.data.results);
                    this.elements = r.data.results;
                    this.elements.original_language = '../assets/img/flags/'+this.elements.original_language+'.png'
                })
                .catch(e=>{
                    console.log(e)
                })
        },
        
        getApi(searchInput){
            console.log(searchInput);
            var api;
            if(this.selection === 'films'){
                api = 'https://api.themoviedb.org/3/search/movie?api_key=80d8049aea831dd859481c955e96072b&language=en-US&query='+ searchInput+'&page=1&include_adult=false'
            }
            else if(this.selection === 'series'){
                api = 'https://api.themoviedb.org/3/search/tv?api_key=80d8049aea831dd859481c955e96072b&language=en-US&query='+ searchInput+'&page=1&include_adult=false'
            }
            console.log(api);
            this.myApi = api
            if(this.reset == 1){
                this.reset = 0
            }
            this.launchApi();
            console.log(this.reset);
        }
    },

    computed :{
        resett(){
            console.log(this.reset);
            var x =this.reset
            return x
        }
    }
}
</script>

<style>

</style>