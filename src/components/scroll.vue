<template>
    <div class="scroll-container">
        <div class="left" @click="$emit('scrollLeft')">
            <div class="scroll-left"> 
                <img src="../assets/img/carets/caret-left-solid.svg" alt="">
                <div v-if="x==0" class="return">
                    <p>End</p>
                </div>
            </div>
        </div>    
        <div class="right" @click="$emit('scrollRight')">  
            <div class="scroll-right"> 
                <img src="../assets/img/carets/caret-right-solid.svg" alt="">
                <div v-if="x==15" class="return">
                    <p>Start</p>
                </div>
            </div>
        </div>  
    </div>
</template>

<script>
export default {
    name : 'scroll',

    props:{
        x : Number,
        y : Number        
    }
}
</script>

<style>

</style>