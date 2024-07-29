<template>
<h1>
  Hello!
</h1>
<p>Press the button to play</p>
<p>Try to click the block as soon as it appears</p>
<button class="play-button" @click="play" :disabled="isPlaying" > {{ buttonText }}</button>
<Block v-if="isPlaying" :delay="delay" @end="endGame"></Block>
<Result :score="score" v-if="showResult"></Result>
</template>

<script>

import Block from './components/Block.vue'
import Result from './components/Result.vue';
export default {
  name: 'App',
  data(){
    return{
      isPlaying:false,
      delay:null,
      score:null,
      showResult:false,
      buttonText:'Play'
    }
  },
  components: {
    Block,Result
  },
  methods:{
    play(){
      this.delay= 2000 +Math.random() *3500;
      this.isPlaying =true;
      this.showResult=false,
      this.buttonText = 'Playing...'; 
    },
    endGame(reactionTime){
      this.isPlaying=false;
      this.score=reactionTime;
      this.showResult=true
      this.buttonText='Play again'
    }
  },
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
.play-button {
  background-color:  plum; 
  border: none;
  color: white;
  padding: 15px 32px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
  margin: 4px 2px;
  cursor: pointer;
  border-radius: 12px;
  transition-duration: 0.4s;
}

.play-button:hover {
  background-color: white;
  color: black;
  border: 2px solid  plum;
}

.play-button:disabled {
  background-color: #cccccc;
  color: #666666;
  cursor: not-allowed;
}
</style>
