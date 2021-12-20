<template>
  <h1>Timer Reaction Game</h1>
  <button @click="start" :disabled="isPlaying">Play</button>

  <Block v-if="isPlaying" :delay="delay" @end="endGame"/>
  <Results v-if="showResults" :score="score"/>
</template>

<script>
import Block from './components/Block.vue'
import Results from './components/Results.vue'

export default {
  name: 'App',
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false,
    }
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000;
      this.isPlaying = true;
      this.score = null,
      console.log(this.delay);
      console.log(this.isPlaying);
    },

    endGame(reactionTime) {
      this.score = reactionTime;
      this.showResults = true;
      this.isPlaying = false;
    }
  },
  components: {
    Block,
    Results,
  },

  
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

button {
  color: white;
  border: none;
  padding: 8px 16px;
  background: #0faf87;
  border-radius: 4px;
  font-size: 16px;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 10px;

}

button[disabled] {
  opacity: 0.2;
  cursor: not-allowed
}
</style>
