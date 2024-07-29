<template>
  <div class="block" v-if="show" @click="stopTimer">
   Click me
  </div>
</template>

<script>
export default {
   props:['delay'],
   data(){
      return{
         show:false,
         timer:null,
         reactionTime:null
      }
   },
   mounted(){
      setTimeout(() => {
         this.show = true;
         this.startTimer();    
      }, this.delay);
   },
   methods:{
     startTimer(){
      this.timer=setInterval(()=>{
         this.reactionTime+=10
      },10)
     },
     stopTimer(){
      clearInterval(this.timer);
      this.$emit('end',this.reactionTime)
     }
   }
}
</script>

<style scoped>
.block{
   width: 400px;
   border-radius: 20px;
   text-align: center;
   background-color: plum;
   margin: 20px auto;
   padding: 100px 0;
   color: white;
}



</style>