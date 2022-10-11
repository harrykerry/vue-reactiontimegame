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
        if(this.score>=1.51){
            this.rank = "Too slow fam"
        }else if(this.score <=1.5 && this.score >=0.51){

            this.rank = "Average Speed - Jaribu Tena"

        }else if(this.score <=1 && this.score >=0.5){

            this.rank = "Almoooost there"
        }else{
            this.rank = "That was fast. Sawasawa Bazuu!!!"
        }
    }
  

}
</script>

<style scoped>


</style>