<template>
  <h1>Click as fast as possible</h1>
  <button @Click="showButton" :disabled="isPlaying">Play</button>
  <br>
  <resultShower v-if="showScore" :score="score"/>
  <blockButton v-if="isPlaying" :delay="delay" @endGame="endHandler"/>
</template>

<script>

import blockButton from './components/blockButton.vue'
import resultShower from './components/resultShower.vue'

export default {
  name: 'App',
  data(){
    return{
      isPlaying:false,
      delay:0,
      score:0,
      showScore:false
    }
  },
  components:{
    blockButton,resultShower
  },
  methods:{
    showButton(){
      this.isPlaying=true;
      this.showScore=false;
      this.delay=2000+Math.random()*5000;
      console.log(this.delay);
    },
    endHandler(reactionTime){
      this.score=reactionTime;
      this.isPlaying=false;
      this.showScore=true
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
  color: #2c3e50;
  margin-top: 60px;
}
</style>
