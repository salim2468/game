<template>
  <div class="block" v-if="show" @click="stopTimer">
    Click
  </div>
</template>

<script>
export default {
    props:['delay'],
    data(){
        return{
            show:false,
            timer:null,
            reactionTime:0, 
            }
    },
    mounted(){
        console.log('components mounted');
        setTimeout(()=>{
            this.show = true;
            this.startTimer();
            console.log(this.delay);
        }, this.delay);
    },
    methods:{
        startTimer(){
            this.timer = setInterval(()=>{
                this.reactionTime +=10;
            },10);
        },
        stopTimer(){
            clearInterval(this.timer);
            console.log(this.reactionTime);
            this.$emit('end',this.reactionTime);
        },
    }

}
</script>

<style>
    .block {
        width: 200px;
        border-radius: 10px;
        background: green;
        color: wheat;
        text-align: center;
        margin: 40px auto;
        padding: 100px 0;
    }

</style>