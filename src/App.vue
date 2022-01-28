<template>
  <h1>Ninja Reaction Timer</h1>
  <button class="btn" @click="start" v-bind:disabled="isPlaying">play</button>
	<Block v-if="isPlaying" :delay="delay" @end="endGame" />
	<Results v-if="showResults" :score="score" />
</template>

<script>
import Block from './components/Block.vue'
import Results from './components/Results.vue'

export default {
  name: 'App',
	components: {
		Block,
		Results
	},
  data() {
	  return {
			isPlaying: false,
			delay: null,
			score: null,
			showResults: false
	  }
  },
  methods: {
	  start() {
			this.delay = 2000 + (Math.random() * 5000)
			this.isPlaying = true
			this.showResults = false
	  },
		endGame(reactionTime) {
			this.score = reactionTime
			this.isPlaying = false
			this.showResults = true
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

.btn {
	padding: 10px 20px;
	border-radius: 5px;
	border: none;
	background: #444;
	color: #fff;
	font-size: 16px;
	cursor: pointer;
}
.btn[disabled] {
	opacity: 0.2;
	cursor: not-allowed;
}
.btn:hover {
	opacity: 0.8;
}
</style>
