<template>
  <h1>Reaction Game</h1>
  <button @click="start" class="play" :disabled="isPlaying">Play</button>
  <Block v-if="isPlaying" :delay="delay" @endGame="displayResults" />
  <h1 v-if="showScore">Your reaction is {{ result }} ms</h1>
</template>

<script>
import Block from './components/Block.vue'
export default {
  name: 'App',
  components: { Block },
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
      this.delay = 2000 + Math.random()*5000
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
