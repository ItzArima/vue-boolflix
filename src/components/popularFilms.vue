<template>
    <div class="films-container popular-films">
        <div class="popular-title">
            <h1>Most Popular Films</h1>
        </div>
        <scroll @scrollRight="scrollRight" @scrollLeft="scrollLeft" :x="this.x" />
        <div class="results-container">
            <div v-for="film in slicePopular" :key="film.id" class="film">
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
                        <div class="language-container">
                            <p>Language -</p>
                            <p>{{film.original_language}}</p>
                            <img :src="require(`../assets/img/flags/${film.original_language}.png`)" alt="">
                        </div>
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
    import votes from './votes'
    import scroll from './scroll'

    export default{
        name : 'popularFilms',


        data(){
            return{
                popular : [],
                x : 0,
                y : 4
            }
        },

        components:{
            votes,
            scroll
        },

        mounted() {
            axios
                .get('https://api.themoviedb.org/3/discover/movie?api_key=80d8049aea831dd859481c955e96072b&language=en-US&sort_by=popularity.desc&include_adult=false&include_video=false&page=1&with_watch_monetization_types=flatrate')
                .then(resp => {
                    console.log(resp.data.results);
                    this.popular = resp.data.results
                })
                .catch(e=>{
                    console.log(e)
                })          
        },

        computed:{
            slicePopular(){
                return this.popular.slice(this.x , this.y);
            }
        },

        methods:{
            scrollRight(){
                if(this.x < 15){
                    this.x +=1
                    console.log("x="+this.x);
                    this.y +=1
                    console.log("y="+this.y);
                }
                else{
                    this.x = 0
                    console.log("x="+this.x);
                    this.y = 4
                }
            },

            scrollLeft(){
                if(this.x > 0){
                    this.x -=1
                    console.log("x="+this.x);
                    this.y -=1
                    console.log("y="+this.y);
                }
                else{
                    this.x = 15
                    console.log("x="+this.x);
                    this.y = 19
                }
            }
        }
    }
</script>

<style>
    
</style>