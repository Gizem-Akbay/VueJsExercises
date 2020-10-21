<template>
  <div class="card">
    <img class="imgs" v-if="card.turn || card.matched" :src="require(`../assets/${card.image}`)" />
    <img class="front-side" v-else :src="require('../assets/front-side.jpg')">
  </div>
</template>
<script>
  export default{
    props : ["card", "index"],
  }
</script>
<style scoped>
  .card{
    width: 135px;
    height: 155px;
    border-radius: 5px;
    border: 1px solid #666;
    transition: box-shadow .5s;
    margin: 15px
  }
  .card:hover{
    box-shadow: 0px 5px 48px #666;
    transition: box-shadow .5s;
  }
  .imgs{
    width: 100%;
    height: 100%;
    object-fit: scale-down;
  }
  .front-side{
    width: 100%;
    height: 100%;
    object-fit: cover;
  }
</style>
