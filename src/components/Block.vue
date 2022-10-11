<template>
<div class="borders">
  <div id="imagery">
    <p @click="stopTimer" v-if="showBlock"></p>
  </div>
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
      calcu: null,
      leftside:null,
      topside:null,
      box:null
    };
  },

  mounted() {
    setTimeout(() => {
      this.showBlock = true;

      this.topside = this.getRandomInt(301,421);
      this.leftside = this.getRandomInt(20,350);
      
      this.box = document.getElementById('imagery');
      this.positionElement(this.box,this.leftside,this.topside);

      this.startTimer();
    }, this.delay);
  },

  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.calcu = this.reactTime += 10;

        this.reactionTime = this.calcu / 1000;
      }, 10);
    },

    stopTimer() {
      clearInterval(this.timer);
      this.$emit("end", this.reactionTime);
    },

    positionElement(el, x, y) {
      el.style.position = "absolute";
      el.style.left = x + "px";
      el.style.top = y + "px";
    },

  getRandomInt(min, max) {
  min = Math.ceil(min);
  max = Math.floor(max);
  return Math.floor(Math.random() * (max - min + 1) + min);
}
  },
};
</script>

<style scoped>
p{
  width: 20px;
  height: 20px;
  border-radius: 50px;
  background-color: yellow;
  border:solid 2px black
  
}
#imagery{
 
  max-width: 200px;
}

.borders{
  margin-top: 80px;
  height: 200px;
}
</style>