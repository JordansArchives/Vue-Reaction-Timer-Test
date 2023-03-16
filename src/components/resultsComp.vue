<template>
    <div>
        <p v-if="showResults">reaction time: {{ score }} ms</p>
        <p class="rankClass"> {{ rank }}</p>
    </div>
</template>
<script>
export default {
    data(){
        return {
            rank: null
        }
    },
    props:['score','showResults'],
    mounted(){
        if (this.score <= 250){
            this.rank = 'Ninja Fingers'
        }
        else if (this.score <= 400){
            this.rank = "Rapid Reflexes"
        }
        else {
            this.rank = "Snail Pace..."
        }
    }
}
</script>
<style scoped>
    p {
  text-align: center;
  margin: 10px;
}

.rankClass {
    font-size: 24px;
    color: #c65555;
    text-align: center;
}
</style>