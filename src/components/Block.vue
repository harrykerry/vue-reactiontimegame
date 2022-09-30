<template>
  <div class="mt-5 squareContent" v-if="showBlock">
    <p id="para" @click="stopTimer"></p>
  </div>
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
    }
    // calcPosition(){

    //   return{
    //     top : (_.random(0, 230)) + 'px',
    //     left: (_.random(0, 210)) + 'px'
    //   }

    
    
  }
};
</script>

<style scoped>
.squareContent {
  display: flex;
  justify-content: center;
  align-items: center;
}

p {
  background-color: yellow;
  width: 50px;
  height: 50px;
  display: flex;
  justify-content: center;
  align-items: center;
  border-radius: 50px;
}
</style>