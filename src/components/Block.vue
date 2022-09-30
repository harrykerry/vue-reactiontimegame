<template>
  <div class="mt-5 squareContent" v-if="showBlock">
    <p @click="stopTimer" >Click Here</p>

  
  </div>
</template>

<script>
export default {

  props:['delay'],

  data(){

    return{
      showBlock:false,
      timer:null,
      reactionTime:0
    }

  },

  mounted(){

    setTimeout(()=>{
      this.showBlock = true
     this.startTimer()
    },this.delay)
  },

  methods:{
    startTimer(){

     this.timer = setInterval(()=>{this.reactionTime += 10},10)

    },

    stopTimer(){

      clearInterval(this.timer)
     this.$emit('end',this.reactionTime)

    }
  }

}
</script>

<style scoped>

.squareContent{

  display: flex;
  justify-content: center;
  align-items: center;

}

p{

  background-color: yellow;
  width: 100px;
  height: 100px;
  display: flex;
  justify-content: center;
  align-items: center;
 
}


</style>