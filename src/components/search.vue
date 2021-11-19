<template>
    <div class="content-container">
        <div class="search-container">
            <label for="Search">Search {{selection}}</label>
            <input type="text" name="Search" v-model="searchInput" :placeholder="'Serach '+this.selection" />
            <button @click="$emit('runApi',searchInput)">Search</button>
        </div>
    </div>
</template>

<script>
export default {
    name : 'search',

    data(){
        return{
            searchInput : "",
        }
    },

    props:{
        selection:String,
    }

}
</script>

<style>

</style>