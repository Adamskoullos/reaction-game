<template>
    <h1 class="time">{{ result }} ms</h1>
    <h2 class="feedback">{{ feedback }}</h2>
</template>

<script>
export default {
    props: ['result'],
    data(){
        return{
            feedback: ''
        }
    },
    mounted(){
        if(this.result < 300){
            this.feedback = 'Smokin...there is a new sherif in town!'
        }
        if(this.result >= 300 && this.result < 400){
            this.feedback = 'Super Sharp Shooter!'
        }
        if(this.result > 400){
            this.feedback = `Sucker....don't give up your day job`
        }
    }
}
</script>

<style>
    .time{
        color: rgb(39, 39, 39);
    }
    .feedback{
        color: rgb(68, 68, 68);
        font-style: italic;
    }
</style>