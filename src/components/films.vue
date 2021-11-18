<template>
    <div class="films-container">
        <search @runApi="getApi"/>
        <div class="results-container">
            <div v-for="film in elements" :key="film.id" class="film">
                <img :src="'https://image.tmdb.org/t/p/w300'+film.poster_path" alt="" srcset="">
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

    data(){
        return{
            elements : [],
            myApi : '',
        }
    },

    methods :{
        launchApi(){
            axios
                .get(this.myApi)
                .then(r => {
                    console.log(r.data.results);
                    this.elements = r.data.results;
                })
                .catch(e=>{
                    console.log(e)
                })
        },
        
        getApi(searchInput){
            console.log(searchInput);
            var api = 'https://api.themoviedb.org/3/search/movie?api_key=80d8049aea831dd859481c955e96072b&language=en-US&query='+ searchInput+'&page=1&include_adult=false'
            console.log(api);
            this.myApi = api
            this.launchApi();
        }
    }
}
</script>

<style>

</style>