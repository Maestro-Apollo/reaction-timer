<template>
  <h1>Reaction Timer Game</h1>
  <p>Click as soon as you see block</p>
  <button @click="start" :disabled="isPlaying">Play</button>
    <Block v-if="isPlaying" :delay="delay" @stop="endGame"></Block>
<!--    <p v-if="showResult">Score Time {{score}} ms</p>-->
    <Result v-if="showResult" :score="score"></Result>
</template>

<script>
import Block from "@/components/Block.vue";
import Result from "@/components/Result.vue";

export default {
  name: 'App',
  components: {
    Result,
    Block
  },
  data(){
  return {
    isPlaying: false,
    delay: null,
    score: 0,
    showResult: false,
  }
},
  methods: {
    start(){
      this.delay = 2000 + Math.random() * 5000;
      this.isPlaying = true;
      this.showResult = false;
    },
    endGame(reactionTime){
      this.score = reactionTime;
      this.isPlaying = false;
      this.showResult = true;
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;
}
</style>
