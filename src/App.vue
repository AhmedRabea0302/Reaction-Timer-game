<template>
  <h1>Timer Reaction Game</h1>
  <button @click="start">Play</button>

  <div v-if="isPlaying">
    <Block :delay="delay" />
  </div>
</template>

<script>
import Block from './components/Block.vue'
import Results from './components/Results.vue'

export default {
  name: 'App',
  data() {
    return {
      isPlaying: false,
      delay: null
    }
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000;
      setTimeout(() => this.isPlaying = true, this.delay)

      console.log(this.delay);
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
</style>
