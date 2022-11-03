<template>
<div class="result-container">

    <div class="time">
        <p class="mt-3">Your time is {{score}} Seconds</p>

    </div>

    <div class="rank"><p>{{rank}} {{nickname}}</p></div>

</div>

<div class="ranking-table">
    <table class="table table-bordered table-success">
  <thead>
    <tr>
      <th scope="col">#rank</th>
      <th scope="col">Nickname</th>
      <th scope="col">Time</th>
     
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">1</th>
      <td>Mark</td>
      <td>0.3S</td>
      
    </tr>
    <tr>
      <th scope="row">2</th>
      <td>Jacob</td>
      <td>1.7S</td>
      
    </tr>
  </tbody>
</table>
</div>
  

</template>

<script>
export default {

    props:['score','nickname'],
    data(){
        return{
            rank:null
        }
    },
    mounted(){
        if(this.score>=1.51){
            this.rank = "Too slow"
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
.time{
    display: flex;
    align-items: center;
    justify-content: center;

}

.rank{
    display: flex;
    align-items: center;
    justify-content: center;


}




</style>