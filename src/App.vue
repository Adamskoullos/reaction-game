<template>
  <h1>Reaction Game</h1>
  <button @click="start" class="play" v-if="!isPlaying">Play</button>
  <Block v-if="isPlaying" :delay="delay" @endGame="displayResults" />
  <Results v-if="showScore" :result="result" />
</template>

<script>
import Block from './components/Block.vue'
import Results from './components/Results.vue'
export default {
  name: 'App',
  components: { Block,  Results },
  data(){
    return {
      isPlaying: false,
      delay: null,
      result: 0,
      showScore: false
    }
  },
  methods: {
    start(){
      this.delay = 1000 + Math.random()*5000
      this.isPlaying = true
      this.showScore = false
    },
    displayResults(reactionTime){
      this.result = reactionTime
      this.isPlaying = false
      this.showScore = true
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;
}
.play{
        width: 100px;
        border-radius: 10px;
        background: green;
        color: #fff;
        text-align: center;
        padding: 20px;
        margin: 40px auto;
        font-size: 2rem;
    }
</style>
