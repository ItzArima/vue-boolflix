<template>
    <div class="main-container">
        <h1>Welcome to Ros</h1>
        <films v-if="selection == 'films'" :selection="selection"/>
        <series v-else-if="selection == 'series'" :selection="selection" />
        <home v-else-if="selection == 'home'" />
    </div>
</template>

<script>
import films from './films.vue'
import series from './series.vue'
import home from './home.vue'

export default {
    name: "siteMain",
    components :{
        films,
        series,
        home,
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