<template>
    <div class="films-container">
        <search @runApi="getApi" :selection="selection" @gFilter="gFilter" :visibility="fVisible"/>
        <div class="results-container">
            <div v-for="film in filterElements" :key="film.id" class="film">
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
                        <h2>{{film.title}}</h2>
                        <div class="original-title-container">
                            <p>{{film.original_title}}</p>
                        </div>
                        <casts :id="film.id"/>
                        <div class="language-container">
                            <p>Language -</p>
                            <p>{{film.original_language}}</p>
                            <img :src="require(`../assets/img/flags/${film.original_language}.png`)" alt="">
                        </div>
                        <h3>Genres:</h3>
                        <genres :genresArray="film.genre_ids"/>
                        <div class="vote-container">
                            <p>Vote -</p>
                            <votes :vote ="film.vote_average"/>
                        </div>
                        <h3>Overview:</h3>
                        <div class="overview-container">
                            
                            <p>{{film.overview}}</p>
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
import casts from './casts.vue'
import genres from './genres.vue'

export default {
    name : 'films',

    components :{
        search,
        votes,
        casts,
        genres
    },

    props:{
        selection : String,
    },

    data(){
        return{
            elements : [],
            myApi : '',
            resetElement : '',
            filter : "",
            fVisible : false
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
            if(searchInput !=""){
                console.log(searchInput);
                var api = api = 'https://api.themoviedb.org/3/search/movie?api_key=80d8049aea831dd859481c955e96072b&language=en-US&query='+ searchInput+'&page=1&include_adult=false';
                console.log(api);
                this.myApi = api
                this.launchApi();
                this.fVisible = true
            }
        },

        gFilter(select){
            console.log(select);
            this.filter = select
        }
    },

    computed:{
        filterElements(){
            if(this.filter != ""){
                let filtering = this.elements.filter(element => {
                    return (element.genre_ids.includes(this.filter))
                })
                return filtering
            }
            else{
                return this.elements
            }
        }
    }
}
</script>

<style>

</style>