<template>
    <div class="content-container">
        <div class="search-container">
            <label for="Search">Search a film</label>
            <input type="text" name="Search" v-model="searchInput" placeholder="Serach a film" />
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
    }

}
</script>

<style>

</style>