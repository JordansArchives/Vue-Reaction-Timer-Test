<script>
import blockComp from './components/blockComp.vue'
import resultsComp from './components/resultsComp.vue'

export default{
  data(){
    return{
      isplaying: false,
      delay: null,
      score: null,
      showResults: false
    }
  },
  methods:{
    start(){
      this.delay = 2000 + Math.random() * 5000
      this.isplaying = true;
      this.showResults = false
      console.log(this.delay)
    },
    endBlock(reactionTime){
      this.score = reactionTime
      this.isplaying = false
      this.showResults = true
    }
  },
  components:{
    blockComp, resultsComp
  }
}
</script>

<template>
  <h1>Ninja Reaction Timer</h1>
  <div class="alignBox">
    <button @click="start" :disabled="isplaying">Start</button>
  </div>
  <blockComp v-if="isplaying" :delay="delay" @end="endBlock"/>
  <resultsComp v-if="showResults" :score="score" :showResults="showResults"/>
</template>

<style scoped>
h1{
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.alignBox{
  margin: 10px;
  display:flex;
  justify-content: center;
  align-items: center;
}

p {
  text-align: center;
  margin: 10px;
}
</style>
