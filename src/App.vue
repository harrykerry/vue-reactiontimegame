<template>

<div class="content container mt-5">



  <div class="form-details mt-3">

   
       <form>
      <h1>Harry Reaction Time Game</h1>

    <div class="form-group mt-5">
    <input type="text" id="name" class="form-control" placeholder="Enter your nickname" v-if="isName" v-model="nickname">
    </div>
 <button @click="toggleBlock();rankPlayer()" :disabled="isPlaying" class="btn btn-success mt-3 " type="submit">Play</button>
   
  </form>
    </div>
  

   <Block v-if="isPlaying" :delay="delay" @end="endGame"/>

     <Results v-if="showResults" :score="score" :nickname='nickname' />
</div>
    
  
</template>

<script>

import Block from './components/Block.vue'
import Results from './components/Results.vue'
import axios from 'axios'

export default {
  name: 'App',
  components:{Block,Results},
  data(){
    return{
     isPlaying:false,
     isName:true,
      delay:null,
      score:null,
      showResults: false,
      nickname: null,
    }
  },
  methods:{
    toggleBlock(){

      this.isPlaying = true
      this.isName= false  
      this.delay = 1000 + Math.random() * 6000
      this.showResults= false
    
    },
    endGame(reactionTime){

      this.score = reactionTime
      this.isPlaying = false
      this.showResults = true

    },

    rankPlayer(){
     axios.post(
      "http://127.0.0.1:8000/api/nickname",
      {nickname: this.nickname},
      ).then(response=>{

        

      })
      
    }
  }

}
</script>

<style scoped>

button{
  width:100%;
}

::placeholder{
  text-align: center;
}

/* .content{
  border: solid 3px black;
  height: 80vh;
} */

.form-details{
  display:flex;
  justify-content: center;
  align-items: center;
}

</style>
