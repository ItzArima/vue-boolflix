<template>
    <div class="filter-search-container">
        <div class="search-container">
            <label for="Search">Search {{selection}}</label>
            <input type="text" name="Search" v-model="searchInput" :placeholder="'Serach '+this.selection" />
            <button @click="$emit('runApi',searchInput)">Search</button>
        </div>
        <div class="filter-container" v-if="visibility == true">
            <label for="filter">Filter categories</label>
            <select name="filter" v-model="select" @change="$emit('gFilter',select)">
                <option value="">All</option>
                <option v-for="element in genres" :key="element.id" :value="element.id">{{element.name}}</option>
            </select>
        </div>
    </div>
</template>

<script>
import axios from 'axios'
export default {
    name : 'search',

    data(){
        return{
            searchInput : "",
            select : "",
            genres :[]
        }
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
    
    props:{
        selection:String,
        visibility : Boolean
    }

}
</script>

<style>

</style>