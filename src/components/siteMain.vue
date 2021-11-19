<template>
    <div class="main-container">
        <h1>Welcome to Ros</h1>
        <films :selection="this.selection"/>
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
};
</script>

<style>
</style>