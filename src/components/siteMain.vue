<template>
    <div class="main-container">
        <h1>Welcome to Ros</h1>
        <films v-if="selection == 'films'" :selection="selection" :reset="reset"/>
        <series v-else-if="selection == 'series'" :selection="selection" />
    </div>
</template>

<script>
import films from './films.vue'
import series from './series.vue'

export default {
    name: "siteMain",
    components :{
        films,
        series,
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