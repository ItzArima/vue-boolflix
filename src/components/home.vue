<template>
    <div class="home-container">
        <div class="video-container">
            <video autoplay loop muted>
                <source src="../assets/videos/cineros-vieo-loop.mp4">
            </video>
            <div class="video-text">
                <h1>WELCOME TO <em>CINEROS</em></h1>
                <p>The portal of films and series</p>
            </div>
        </div>    
        <div class="home-content">
            <popularFilms />
            <popularSeries />
        </div>    
  </div>
</template>

<script>
import popularFilms from './popularFilms'
import popularSeries from './popularSeries'
export default {   
    name : 'home',
    components:{
        popularFilms,
        popularSeries
    }
}
</script>

<style>

</style>