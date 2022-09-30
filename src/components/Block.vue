<template>
 
    <p><img src="../assets/aki.gif" id="para" class="mt-5" @click="stopTimer" v-if="showBlock"></p>
 
</template>

<script>
export default {
  props: ["delay"],

  data() {
    return {
      showBlock: false,
      timer: null,
      reactTime: 0,
      calcu:null
    };
  },

  mounted() {

    console.log("Mounted")
    setTimeout(() => {

      this.showBlock = true;

      this.startTimer();
    }, this.delay);

  },


  methods: {
    startTimer() {
      this.timer = setInterval(() => {
       this.calcu =  this.reactTime += 10;

       this.reactionTime = (this.calcu) / 1000;
       
      }, 10);
    },

    stopTimer() {
      clearInterval(this.timer);
      this.$emit("end", this.reactionTime);
    },


    
  }
};
</script>

<style scoped>

img {

  width: 80px;
  height: 80px;
  border-radius: 50px;
}



</style>