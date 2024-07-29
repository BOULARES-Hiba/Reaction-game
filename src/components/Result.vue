<template>
  <p> Reaction time : {{ score }} ms</p>
  <p class="Crank">{{ rank }}</p>
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
      if (this.score < 250) {
         this.rank= 'You are really fast';
      } 
      else if ( this.score < 400) {
         this.rank='Rapid Reflexes';
      }
       else {
        this.rank='You are SLOW';
      }
   }

}
</script>

<style>
   .Crank{
      font-size: 1.5rem;
      font-weight: bold;
      color: rgb(244, 3, 244);
   }
</style>