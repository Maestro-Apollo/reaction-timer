<script>
  export default {
    props:['delay'],
    data(){
      return{
        showBlock: false,
        timer: null,
        reactionTime: 0,
      }
    },
    mounted(){
      setTimeout(() =>{
        this.showBlock = true;
        this.startTimer();
      }, this.delay);
    },
    methods:{
      startTimer(){
      this.timer = setInterval(() =>{
        this.reactionTime += 10
      },10);
      },
      stopTimer(){
        clearInterval(this.timer);
        this.$emit('stop', this.reactionTime);
      }
    }

  }

</script>

<template>
  <div class="block" v-if="showBlock" @click="stopTimer">
    click me
  </div>
<!--  <p>{{delay}}</p>-->
</template>

<style scoped>
  .block{
    width: 480px;
    border-radius: 20px;
    background-color: darkcyan;
    color: white;
    padding: 100px 0;
    margin: 40px auto;
  }
</style>