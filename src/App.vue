<template>
<div class="mt-3">
  <h1>Harry Reaction Time Game</h1>
  <h2>Built this while learning Vue </h2>
  <h1>Click on the Yellow Dot (Making changes, mnaiba sana😎)</h1>
   
    <button @click="toggleBlock" :disabled="isPlaying" class="btn btn-primary mt-5">Play Me</button>


     <Block v-if="isPlaying" :delay="delay" @end="endGame"/>

     <Results v-if="showResults" :score="score"/>

    
  
</div>
  
</template>

<script>

import Block from './components/Block.vue'
import Results from './components/Results.vue'

export default {
  name: 'App',
  components:{Block,Results},
  data(){
    return{
     isPlaying:false,
      delay:null,
      score:null,
      showResults: false
    }
  },
  methods:{
    toggleBlock(){

      this.isPlaying = true  
      this.delay = 2000 + Math.random() * 7000
      this.showResults= false
    
    },
    endGame(reactionTime){

      this.score = reactionTime
      this.isPlaying = false
      this.showResults = true

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
