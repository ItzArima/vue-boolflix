<template>
    <div class="main-container">
        <h1>Welcome to Ros</h1>
        <div class="content-container">
            <div class="search-container">
                <label for="Search">Search a film</label>
                <input type="text" name="Search" placeholder="Serach a film" />
                <button>Search</button>
            </div>
            <div class="films-container">
                <films />
            </div>
        </div>
    </div>
</template>

<script>
import films from './films.vue'

export default {
    name: "siteMain",
    components :{
        films
    }
};
</script>

<style>
</style>