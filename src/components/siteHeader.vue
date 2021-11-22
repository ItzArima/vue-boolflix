<template>
    <div class="header-container">
        <div class="logo-container" @click="$emit('selection','home')">
                <h1 class="thin">CINE</h1>
                <h1 class="bold">ROS</h1>
        </div>
        <div class="nav-container">
            <p @click="$emit('selection','home')">Home</p>
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