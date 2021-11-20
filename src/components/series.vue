<template>
    <div class="films-container">
        <search @runApi="getApi" :selection="selection"/>
        <div class="results-container">
            <div v-for="film in elements" :key="film.id" class="film">
                <div  class="img-container"> 
                    <div class="film-image">
                        <div v-if="film.poster_path != null" class="image-verifier">   
                            <img :src="'https://image.tmdb.org/t/p/w300'+film.poster_path" alt="" srcset="">
                        </div>    
                        <div v-else class="no-image">
                            <h1>No Image</h1>
                        </div>
                    </div>
                    <div class="film-infos">
                        <h2>{{film.name}}</h2>
                        <div class="original-title-container">
                            <p>{{film.original_name}}</p>
                        </div>
                        <div class="language-container">
                            <p>Language -</p>
                            <p>{{film.original_language}}</p>
                            <img :src="require(`../assets/img/flags/${film.original_language}.png`)" alt="">
                        </div>
                        <div class="vote-container">
                            <p>Vote -</p>
                            <votes :vote ="film.vote_average"/>
                        </div>
                    </div>    
                </div>    
            </div>
        </div>
    </div>
</template>

<script>
import axios from 'axios'
import search from './search.vue'
import votes from './votes.vue'

export default {
    name : 'series',

    components :{
        search,
        votes,
    },

    props:{
        selection : String,
    },

    data(){
        return{
            elements : [],
            myApi : '',
            resetElement : ''
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
            var api = api = 'https://api.themoviedb.org/3/search/tv?api_key=80d8049aea831dd859481c955e96072b&language=en-US&query='+ searchInput+'&page=1&include_adult=false'
            console.log(api);
            this.myApi = api
            this.launchApi();
        },


    },
}
</script>

<style>

</style>