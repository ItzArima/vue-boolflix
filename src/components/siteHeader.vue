<template>
    <div class="header-container">
        <div class="logo-container">
              <h1>Ros</h1>
        </div>
        <div class="nav-container">
            <p @click="$emit('films')">Films</p>
            <p @click="$emit('series')">Series</p>
            <p>About Us</p>
        </div>
    </div>
</template>

<script>
export default {
    name : 'siteHeader',

    data(){
        return {
            selection : ""
        }
    }
}
</script>

<style >
    
</style>