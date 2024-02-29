<script>
  export default {
    props: ['score'],
    data(){
      return{
        rank: null,
        animal: null,
        imageUrl: null,
      };
    },

    mounted() {
      if (this.score < 600) {
        this.rank = "Too Fast";
        this.animal = "chita.png";
      } else if (this.score < 700) {
        this.rank = "Fast";
        this.animal = "eagle.webp";
      } else if (this.score < 900) {
        this.rank = "Slow";
        this.animal = "turtle.png";
      } else {
        this.rank = "Too Slow";
        this.animal = "snail.webp";
      }
      this.imageUrl = require(`../assets/${this.animal}`);
    },
  }
</script>

<template>
  <h1>{{this.rank}}</h1>
  <h4>Reaction time {{score/1000}}s</h4>
  <img :src="imageUrl">

  <p>{{animal}}</p>
  <p>{{imageUrl}}</p>
</template>

<style scoped>
img{
  width: 50%;
}
</style>