<template>
    <div class="block" v-if="showBlock" @click ="stopTimer">
        <h1>click me</h1>
    </div>
</template>

<script>
export default {
    data(){
        return{
            showBlock: false,
            timer: null,
            reactionTime: 0
        }
    },
    props: ['delay',],
    mounted(){
        console.log('component mounted')
        setTimeout(() => {
            this.showBlock = true
            this.startTimer()
            console.log(this.delay)
        }, this.delay)
    },
    methods:{
        startTimer(){
            this.timer = setInterval(() => {
                this.reactionTime += 10
            }, 10)
        },
        stopTimer(){
            clearInterval(this.timer)
            console.log(this.reactionTime)
            this.$emit('end', this.reactionTime)
        }
    }
}
</script>
<style>
    .block {
        width:400px;
        height:400px;
        border: solid 5px #c65555;
        background-color: #5f2424;
        border-radius: 20px;
        text-align: center;
        padding: 100px 0;
        margin: 40px auto;
    }
</style>