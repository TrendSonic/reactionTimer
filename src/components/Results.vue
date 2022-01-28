<template>
	<div class="">
		<h1>Reaction Time: {{ score }}ms</h1>
		<h2>{{ rank }}</h2>
	</div>
</template>

<script>
export default {
	props: [ 'score' ],
	data() {
		return {
			rank: null
		}
	},
	mounted() {
		if(this.score < 200) {
			this.rank = 'Ninja fingers'
		} else if(this.score < 350) {
			this.rank = 'Rapid reflexes'
		} else {
			this.rank = 'Too slow...'
		}
	}
}
</script>

<style scoped>
h1 {
	color: green;
}
</style>