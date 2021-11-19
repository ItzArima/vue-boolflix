<template>
  <div class="flag-container">
      <img :src="require(`../assets/img/flags/${film.original_language}.png`)" alt="">
  </div>
</template>

<script>
export default {
    name :'flag',

    props:{
        country: String,
    },
}
</script>

<style>

</style>