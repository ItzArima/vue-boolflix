<template>
    <div class="header-container">
        <div class="logo-container">
              <h1>Ros</h1>
        </div>
        <div class="nav-container">
            <p @click="$emit('selection','films')">Films</p>
            <p @click="$emit('selection','series')">Series</p>
            <p>About Us</p>
        </div>
    </div>
</template>

<script>
export default {
    name : 'siteHeader',

}
</script>

<style >
    
</style>