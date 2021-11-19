<template>
    <div class="main-container">
        <h1>Welcome to Ros</h1>
        <films :selection="this.selection" :reset="this.reset"/>
    </div>
</template>

<script>
import films from './films.vue'

export default {
    name: "siteMain",
    components :{
        films
    },

    data(){
        return{
            fselection : "",
        }
    },

    props :{
        selection : String,
        reset : Number,
    },

    computed:{
        resetting(){
            return this.reset
        }
    }
};
</script>

<style>
</style>