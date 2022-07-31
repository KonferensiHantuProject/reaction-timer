<template>
<h1>Timer Reaction Bone</h1>
<button @click="start" :disabled="isPlaying">Play</button>
<Block v-if="isPlaying" :delay="delay" @akhir="endGame" />
<Result v-if="showResult" :score="score" />
</template>

<script>
// Import component
import Block from './components/Block.vue'
import Result from './components/Result.vue'

export default {
  name: 'App',
  components: {
    Block,
    Result
  },
  data (){
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResult: false
    }
  },
  methods: {
    // When Click the button
    start(){
      this.delay = 2000 + Math.random() * 5000
      this.isPlaying = true
      
      // Restart the score
      this.showResult = false
    },
    endGame(reactionTime) {
      this.score = reactionTime

      // Stop the game
      this.isPlaying = false

      // Menampilkan skor
      this.showResult = true
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
button{
  background: #0faf87;
  color: white;
  border: none;
  padding: 8px 16px;
  border-radius: 4px;
  font-size: 16px;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 10px;
}
button[disabled]{
  opacity: 0.2;
  cursor: not-allowed;
}
</style>
