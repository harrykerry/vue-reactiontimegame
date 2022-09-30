<template>
  <p class="mt-3">Your time is {{score}} Seconds</p>
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
        if(this.score>=2.6){
            this.rank = "Too slow fam"
        }else if(this.score <=2.5 && this.score >=1){

            this.rank = "Average Speed - Jaribu Tena"

        }else{
            this.rank = "Sawasawa Bazuu!!!"
        }
    }
  

}
</script>

<style>

</style>