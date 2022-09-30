<template>
  <p class="mt-3">Your time is {{score}} Milliseconds</p>
  <p>{{rank}}</p>

</template>

<script>
export default {

    props:['score'],
    data(){
        return{
            rank:null
        }
    },
    mounted(){
        if(this.score>=3000){
            this.rank = "You are too slow - Try again 😁"
        }else if(this.score <3000 && this.score >=1000){

            this.rank = "Average Speed - Jaribu Tena"

        }else{
            this.rank = "Sawasawa Bazuu!!!"
        }
    }
  

}
</script>

<style>

</style>