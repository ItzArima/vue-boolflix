<template>
    <div class="main-container">
        <h1>Welcome to Ros</h1>
        <films />
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